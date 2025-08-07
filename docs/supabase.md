# 🪐 Supabase

> **TL;DR:** we use Supabase for image storage because we’re broke.

## Why Supabase?

We needed *somewhere* to toss user-uploaded images (OC pfps, story covers, etc) without triggering Firebase’s **daily cry session** over write quotas. Supabase offered:
- Easy uploads
- CDN hosting
- Public URLs
- ✨free tier ✨

> …so yeah. Supabase is now our low-rent AWS S3.

 

## “Why not use Supabase for *everything*?”

We ***tried.*** God, we tried.

Here's what went down:

1. **Attempt 1:** Firebase + Supabase with JWT token passthrough  
   → worked, for like 20 minutes  
   → then blew up, sessions broke, user IDs didn't sync, cried

2. **Attempt 2:** Full Supabase rewrite  
   → 7 hours of data weirdness, auth failure, and no email fallback  
   → next day: another 2 hours of bugs  
   → we gave up and ran back to Firebase like the guilty little rats we are



## What we use Supabase for *now*

- Uploading user content (images, thumbnails)
- Serving content via public URLs
- Potential fallback for other file types in the future

That’s it. No auth, no metadata, no nonsense. Just… images.



## File Locations
soon
## todo:
backend infra to automate cleaning up unused uploads- because this thing *will* rot if we let it.


## Docs Links

- [Supabase Storage Docs](https://supabase.com/docs/guides/storage)
- [Auth sharing between Firebase + Supabase](https://github.com/supabase/supabase/discussions/13487) (pain post)

markdown
Copy
Edit
