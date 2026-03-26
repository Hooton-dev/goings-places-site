# Goings Places Home Buyers — Website Deployment Guide

## What's In This Package

```
goings-places-site/
├── index.html          ← Homepage (Columbus, GA focused)
├── auburn-al/          ← Auburn, AL landing page
│   └── index.html
├── contact/            ← Contact page with both phone numbers
│   └── index.html
├── blog/               ← Blog index page
│   └── index.html
├── admin/              ← Decap CMS (content management)
│   ├── index.html
│   └── config.yml
├── css/
│   └── style.css       ← All styles
├── js/
│   └── main.js         ← Animations, forms, navigation
├── images/             ← Place your images here
├── _redirects          ← Old URL → new URL mapping
├── sitemap.xml         ← For Google Search Console
├── robots.txt          ← Search engine instructions
├── netlify.toml        ← Netlify configuration
└── README.md           ← This file
```

## BEFORE YOU DO ANYTHING

1. **Replace phone numbers**: Search and replace these placeholder numbers:
   - `(706) 365-0015` → your real Columbus number
   - `7063650015` → same number, no formatting (for tel: links)
   - `(334) 408-1833` → your real Auburn number
   - `3344081833` → same, no formatting

2. **Replace email**: Search for `dave@goingsplaceshomebuyers.com` and replace with your real email

3. **Replace testimonials**: The reviews on the site are placeholders. Replace with your real seller testimonials.
   - Log into Google Business Profile → Reviews
   - Copy the text of your best 3-5 reviews
   - In index.html, find the `<!-- ═══ TESTIMONIALS ═══ -->` section
   - Replace the review text, names, and locations with real ones
   - Keep the HTML structure the same, just change the text inside
   - The site shows your 4.9 star rating with 13 reviews — impressive!

4. **Headshot is included**: Dave's professional headshot is already embedded in the site 
   at `/images/dave-goings-headshot.jpg`. The renovation dinner photo with Rebecca is at 
   `/images/dave-rebecca-renovation-dinner.jpg` and appears in the "Why Dave" section.


## DEPLOYMENT OPTION A: Drag & Drop (Simplest)

1. Go to https://app.netlify.com
2. Sign up / log in
3. Drag this entire `goings-places-site` folder onto the deploy area
4. Your site is live at a random Netlify URL (e.g., happy-cat-123.netlify.app)
5. Test everything on that URL
6. Go to Domain Settings → Add Custom Domain → enter `goingsplaceshomebuyers.com`
7. Follow Netlify's instructions to update your DNS

**Note**: With drag & drop, the blog CMS won't work (it needs GitHub). 
The site itself works perfectly — you just can't write blog posts through the admin panel.


## DEPLOYMENT OPTION B: GitHub + Netlify (Recommended — enables blog CMS)

1. Create a GitHub account (if you don't have one)
2. Create a new repository called `goings-places-site`
3. Upload all these files to that repository
4. In Netlify, click "Import from Git" instead of drag & drop
5. Connect your GitHub account and select the repository
6. Deploy settings: leave everything default, click Deploy
7. After deploy, go to Netlify Dashboard → Identity → Enable Identity
8. Under Identity → Settings → Services → Git Gateway → Enable
9. Go to Identity → Invite Users → invite your email
10. Check your email, set a password
11. Now visit yourdomain.com/admin to write blog posts!


## CONNECTING YOUR DOMAIN

After deploying (either option):
1. In Netlify: Site Settings → Domain Management → Add Custom Domain
2. Enter: goingsplaceshomebuyers.com
3. Netlify gives you nameservers or a CNAME record
4. Log into your domain registrar and update DNS
5. Wait 15 min to 48 hours for propagation
6. Netlify auto-provisions SSL (free HTTPS)


## SETTING UP FORM NOTIFICATIONS

Your lead capture forms already have `data-netlify="true"` which means Netlify 
automatically catches submissions. To get email notifications:

1. Go to Netlify → Site Settings → Forms
2. You'll see "cash-offer" and "auburn-cash-offer" forms listed
3. Under Form Notifications → Add Notification → Email
4. Enter your email address
5. Every form submission now emails you directly

For advanced routing (e.g., to GoHighLevel or a Google Sheet):
1. Go to Netlify → Site Settings → Forms → Form Notifications
2. Add an Outgoing Webhook notification
3. Point it to a Zapier webhook URL
4. In Zapier, route to your CRM / Google Sheet / SMS


## POST-LAUNCH CHECKLIST

□ Update Google Business Profile website URL to goingsplaceshomebuyers.com
□ Submit sitemap in Google Search Console (goingsplaceshomebuyers.com/sitemap.xml)
□ Request indexing of homepage in Search Console
□ Verify forms are working (submit a test entry)
□ Test site on your phone
□ Update any print materials, business cards, mailers
□ Cancel REI Blackbook (only AFTER everything is confirmed working)


## ADDING NEW CITY PAGES

To add a new city (e.g., Opelika, Phenix City):
1. Copy the `auburn-al/` folder
2. Rename it (e.g., `opelika-al/`)
3. Edit the HTML inside — change all Auburn references to the new city
4. Update the sitemap.xml with the new URL
5. Add a link to the new page in the homepage footer and areas section
6. Redeploy


## NEED HELP?

If you get stuck at any point, the Netlify docs are excellent:
https://docs.netlify.com

For Decap CMS setup:
https://decapcms.org/docs/intro/
