---
name: openproject
description: "Set up and use OpenProject, the open-source self-hosted project management suite (work packages, Gantt, Kanban/Scrum boards, time and cost tracking, wiki, meetings), and drive it from Claude Code through its REST API. Use when Dean wants project or task management for client or team work, compares Asana, Jira, MS Project or Monday, needs Gantt timelines or time tracking, or wants Claude to create or update tasks in OpenProject."
metadata:
  pricing: free-self-host
  cost: "Community edition free (GPL, self-host); Enterprise from €5.95/user/mo with a 25-user minimum."
  tags: [project-management, gantt, time-tracking, self-hosted]
---

# OpenProject

[opf/openproject](https://github.com/opf/openproject) (GPL-3.0) is a mature Ruby on Rails + Angular web app for project management. The **Community edition is free** and self-hosted. Enterprise add-ons (team planner, resource and portfolio management, SSO, multiple sprints, MCP server and more) need a paid plan, which starts at 25 users.

## Is it the right tool?

- **Good fit:** a team or agency running several client projects with timelines (Gantt), time and cost tracking, budgets, meeting minutes, and a wish to keep data on its own server.
- **Overkill for solo work.** For Dean alone, GitHub Projects (already next to the code, free), Linear's free tier, or a lighter self-hosted tool like Plane or Vikunja is less to run.
- It feels closer to Jira/MS Project than to Asana: powerful, but denser.

## Set up

- Follow the official install guide (docs at openproject.org/docs/installation-and-operations). It covers Docker Compose for production, a single all-in-one container for evaluation, and Linux packages.
- Use a server with about 4 GB of RAM or more (check the docs' current system requirements). It needs PostgreSQL, a stable hostname and HTTPS for real use.
- Set the secret key, hostname and HTTPS settings exactly as the guide says. Change the default `admin` password on first login.
- Back up the database and attachments on a schedule; the guide has backup commands. Upgrade one major version at a time, following the release notes.

## Drive it from Claude Code (Community edition)

The MCP server is an Enterprise add-on, so on Community use the REST API v3:
- Dean creates an API token under **My account → Access tokens** and gives it to the shell as an env var (`OPENPROJECT_URL`, `OPENPROJECT_TOKEN`). Never commit it or print it.
- Authenticate with basic auth, user `apikey`: `curl -u "apikey:$OPENPROJECT_TOKEN" "$OPENPROJECT_URL/api/v3/projects"`
- Common calls: list work packages `GET /api/v3/projects/{id}/work_packages`, create `POST /api/v3/projects/{id}/work_packages` (JSON with `subject`, `_links.type`, optional `description.raw`), update with `PATCH /api/v3/work_packages/{id}` including the current `lockVersion`. The API is HAL+JSON, so use the `_links` it returns instead of building URLs.
- Typical uses: turn a meeting transcript or client brief into work packages, log progress after a coding session, generate a status summary for a client.
- Read before writing. Show Dean the list of tasks before creating more than a handful, and never bulk-delete.

## Don't

- Don't expose an instance without HTTPS, or with default credentials.
- Don't buy Enterprise just for the MCP server if the REST API covers the need.
