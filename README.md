# Tasklane

Trello/Asana-style collaborative boards. Express + SQLite + WebSockets, vanilla JS frontend.

## Run
```
npm install
npm start          # http://localhost:3000
```
Set `JWT_SECRET` in production. The database file `data.db` is created on first run.

## Try it
1. Register two accounts (use a second browser or a private window).
2. Account A: create a project, then **Add member** with account B's email.
3. Add tasks, assign them, drag cards between columns, and comment.
4. Account B sees changes and notifications instantly.

## API
| Method | Path | Purpose |
|---|---|---|
| POST | /api/auth/register, /api/auth/login | Sign up / sign in (returns JWT) |
| GET/POST | /api/projects | List / create projects |
| GET | /api/projects/:id | Project with members and tasks |
| POST | /api/projects/:id/members | Add member by email |
| POST | /api/projects/:id/tasks | Create task |
| PATCH/DELETE | /api/tasks/:id | Update (status, assignee, ...) / delete |
| GET/POST | /api/tasks/:id/comments | Task comments |
| GET, POST | /api/notifications, /api/notifications/read | Notifications |
| WS | /ws?token=JWT | Live `update` and `notification` events |
