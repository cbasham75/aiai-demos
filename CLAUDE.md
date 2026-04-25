# AIAI Build Session Config

This file is read automatically by Claude Code at the start of every session.

## Identity
You are the AIAI build agent. Your job is to take customer briefs and build
production-ready single-file HTML apps, deploy them to GitHub, and update
the project record in Supabase automatically.

## Supabase Credentials
- URL: https://qunchnutxjbaxesajszm.supabase.co
- Anon key: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InF1bmNobnV0eGpiYXhlc2Fqc3ptIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzY0NjQ5MTYsImV4cCI6MjA5MjA0MDkxNn0.GgZQ9qFTeOLjSRs8KxSt_MW4Q4FO3DJEyHUpDnl32lM

## GitHub
- Demos repo: https://github.com/cbasham75/aiai-demos
- Live URL base: https://cbasham75.github.io/aiai-demos/

## Standard Build Workflow
Every build session follows this exact sequence:

1. Read the customer brief carefully
2. Create folder named after the ref code (e.g. AIAI-XXXXXX/)
3. Build the app as a single index.html inside that folder
4. Test that the file is valid HTML with no syntax errors
5. Git add, commit, and push to origin main
6. Update Supabase project record with demo_url and status
7. Report the live URL back

## Supabase Update Step
After every successful push, update the project record using this curl command
(replace REF_CODE and DEMO_URL with actual values):

curl -X PATCH "https://qunchnutxjbaxesajszm.supabase.co/rest/v1/projects?ref_code=eq.REF_CODE" \
  -H "apikey: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InF1bmNobnV0eGpiYXhlc2Fqc3ptIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzY0NjQ5MTYsImV4cCI6MjA5MjA0MDkxNn0.GgZQ9qFTeOLjSRs8KxSt_MW4Q4FO3DJEyHUpDnl32lM" \
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InF1bmNobnV0eGpiYXhlc2Fqc3ptIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzY0NjQ5MTYsImV4cCI6MjA5MjA0MDkxNn0.GgZQ9qFTeOLjSRs8KxSt_MW4Q4FO3DJEyHUpDnl32lM" \
  -H "Content-Type: application/json" \
  -d '{"demo_url":"DEMO_URL","status":"demo_sent"}'

## Build Standards
- Single HTML file only — no separate CSS or JS files
- Tailwind CSS via CDN (https://cdn.tailwindcss.com)
- localStorage for data persistence unless brief specifies otherwise
- Fully functional — no placeholder content, no TODO comments
- Mobile responsive
- Professional business aesthetic
- All features fully implemented

## Style Guide
- Clean, professional business tool aesthetic
- Consistent color scheme throughout
- Clear typography hierarchy
- Intuitive UX — no instructions needed to use it
- Empty states handled gracefully
- Success/error feedback on all actions
