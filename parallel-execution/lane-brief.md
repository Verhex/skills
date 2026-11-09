# Lane brief: filled example

An invented task, adding password reset to a web application, split into two lanes. The format is plain text
for a person or an agent to read; nothing parses it. Replace every line with your own facts.

## Shared brief (all lanes)

- **Goal:** a signed-out user can reset their password by email.
- **Starting point:** revision `4f2a9c1` of the main branch.
- **Decided before the split, taken as given by every lane:**
  - the reset endpoint is `POST /auth/reset` with a body of `{ token, newPassword }`;
  - a token is valid for 30 minutes and for one use.
- **Nobody may:** merge, deploy, change shared configuration, or edit another lane's paths.
- **Shared resources:**
  - the full test suite runs one lane at a time, through the coordinator's queue;
  - the shared development database is read-only for every lane.
- **Stop and report when:** a decision above turns out to be wrong, a needed file is outside your paths, or
  you hit the limit below.

## Lane A: server

- **Task:** implement token creation, the reset endpoint and its tests.
- **May write:** `server/auth/`, `server/tests/auth/`.
- **May read:** the whole repository.
- **Run-time resources:** its own private test database, created by the lane. Port 4101, exclusive.
- **Owns the decisions:** token storage format, error codes returned by the endpoint.
- **Hand back:** the diff, the output of the auth tests, and the list of error codes for Lane B.
- **Limits:** 40 minutes, two attempts at any failing step.

## Lane B: web client

- **Task:** the "forgot password" screen, the reset form and their tests.
- **May write:** `web/src/auth/`, `web/tests/auth/`.
- **May read:** the whole repository.
- **Run-time resources:** a mocked server only; it does not start the real one. Port 4102, exclusive.
- **Takes as given:** the endpoint shape above. Uses placeholder error codes until Lane A hands back the list.
- **Cannot run:** the browser end-to-end test (no browser in its sandbox). Hands the coordinator the exact
  command and what a pass looks like.
- **Hand back:** the diff, the output of the component tests, and the end-to-end command for the coordinator.
- **Limits:** 40 minutes, two attempts at any failing step.

## Fan-in order

1. Lane A, then Lane B on top of it.
2. `web/src/locales/en.json` and the route table are touched by both lanes: merge as the union of both sides.
3. Replace Lane B's placeholder error codes with Lane A's list.
4. Coordinator runs the full suite and the end-to-end test on the joined result.
