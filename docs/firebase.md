# 🔥 Firebase

Firebase is the emotionally unstable core of Wagyu’s backend.  
Yes, we know it’s proprietary. Yes, we know there are limits.  
No, we don’t have money to leave yet.


## What It Stores

Firebase handles all the “actual data”:

- 👤 User Info (no email storage tho. we're not narcs.)
- 🎭 OCs (plural, people have like 20)
- 🛠️ Servers (basic info + meta keys)
- 🧵 Stories
- 💬 Messages (across multiple projects)
- 🚨 Reports
- 👀 User relations, blocks, etc



## “Why not just shove it all into one project?”

Buddy, we **would** if it didn’t cost money.

### 🚧 Firebase Issues:

- Write-heavy structure
- Global limits apply per project
- Once you get popular... Firebase *punishes* you

So… we split it across **3 Firebase projects**, load-balanced manually.

## Breakdown of Projects

- **Project 1 (Core):** Auth, users, OC metadata, server *headers*
- **Project 2 (Messages A):** Channels, messages, media refs
- **Project 3 (Messages B):** Overflow (2nd shard hehe)

Each server has a field like:
```json
{
  "project_key": "messagesA",
  "server_id": "xyz",
  "channel_refs": [...]
}
```
This lets us keep things in sync... sorta. It's janky, but it works.

# File Links
soon


# Disclaimer
We do not store emails or personally identifying info in our own DB.
Firebase auth handles it all. If Firebase gets pwned, that's on Google, not us.
