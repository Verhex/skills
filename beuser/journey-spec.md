# Journey spec and verdict table: filled example

An invented product, a note-taking app with a web and a mobile client, to show the shape. Replace every line
with your own product's facts.

## Journey spec (written before building)

**Surface:** first sign-up and first shared note.
**Version walked:** filled in at walk time.

### Personas

| Persona | Goal | Skill | Device, language | Tastes |
|---|---|---|---|---|
| Ayla, first-time user | Write a note and share it with one friend | Low; follows what the screen says | Phone, Turkish | Short sentences, one choice per screen |
| Ben, returning user | Share an existing note from a new laptop | High; uses keyboard shortcuts | Web, English | Dense, no tutorials |
| Dana, team admin | Invite three members and limit sharing outside the team | Medium | Web, English | Exact wording about permissions |

### Branch list

| # | Persona | Starting state | Path |
|---|---|---|---|
| 1 | Ayla | No account, good network | Sign up → first note → share by link |
| 2 | Ayla | Sign-up abandoned at email verification yesterday | Return → resume verification → first note |
| 3 | Ayla | No network after sign-up | Write note offline → reconnect → share |
| 4 | Ben | Account exists, new device | Sign in → find note → share by link |
| 5 | Ben | Session expired mid-share | Share → forced sign-in → back to the share dialog |
| 6 | Dana | Team exists, no members | Invite three → restrict outside sharing |
| 7 | Dana as member | Outside sharing restricted | Try to share outside → refusal with next step |

**Dropped combinations:** Ben on phone (same path as branch 4, different layout only; covered by the layout
review). Dana offline (the admin screen requires a connection; refusal is covered by branch 3's offline
message). Approved by the product owner before the walk.

### Steps for branch 7

| Step | The person sees | Choices | Expected outcome | On refusal: cause and next step |
|---|---|---|---|---|
| 1 | Note open, "Share" button | Share | Share dialog opens | n/a |
| 2 | Dialog with a link field and "Anyone with the link" greyed out | Copy team link; hover or tap the greyed option | Team link copied | Greyed option explains: "Your team admin has limited sharing to team members. Ask Dana K. to change it." |

### Twin paths

| Job | Path A | Path B | Must agree on |
|---|---|---|---|
| Share a note | Share button in the note | "Share" in the note list's context menu | Same dialog, same default, same refusal text |
| Invite a member | Admin screen form | CSV import | Same validation errors, same invitation email |

### Borrowed shape

Share dialog follows the pattern of widely used document editors: link field first, access level below it.
Not covered by a proven product: the refusal that names the admin who can change the rule.

## Verdict table (written after the walk)

**Version:** 2.4.0, build 5512. **Instance:** disposable test workspace created by the walker.

| # | Persona | Verdict | Finding | Next step |
|---|---|---|---|---|
| 1 | Ayla | GREEN | none | none |
| 2 | Ayla | RED | Returning after an abandoned verification shows "Email already in use" with no way to resend the code | Add a resend path; walk 1 and 2 again |
| 3 | Ayla | FRICTION | Offline note saves, but nothing says it will sync later | Add a "saved on this device" line, or the owner accepts it |
| 4 | Ben | GREEN | none | none |
| 5 | Ben | GREEN | none | none |
| 6 | Dana | GREEN | none | none |
| 7 | Dana as member | FRICTION | Refusal text is correct, but only appears on hover; no hover on touch | Show the reason inline |

**Result:** not accepted. Branch 2 is RED. Branches 3 and 7 need a fix or the owner's explicit acceptance.
