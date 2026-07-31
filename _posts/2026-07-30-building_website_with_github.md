---
layout: single
title: "How I Built a Free, Custom-Themed Website Using Squarespace and GitHub Pages"
date: 2026-07-28
category: tech
---

With the new phase of our lives kicking off this summer, Onam and I wanted a dedicated space to document our new chapter. We needed a simple hub to share photos and thoughts from our adventures and various projects.

I had already registered our domain, `ronam.us`, through Squarespace. I consider myself fairly tech-savvy, but the nuances of modern web hosting, DNS records, and content management systems were outside my wheelhouse. 

I decided to keep the domain registered with Squarespace, but route the hosting through GitHub, which is a great middle path as it gives an opportunity to learn about this area but not get lost into the details.

Here is the complete, step-by-step breakdown of how I launched a secure, professional-looking site using Jekyll.

### Step 1: The Hosting Strategy
GitHub Pages is designed to host static websites directly from a code repository. It is completely free, highly reliable, and natively supports Jekyll, a static site generator that translates simple text files into fully coded web pages.

1. I created a public repository on GitHub named `rohitdas.github.io`.
2. Under the repository settings, I navigated to **Pages** and set it to deploy from the main branch. 
3. In the **Custom domain** section of those settings, I entered my Squarespace domain: `ronam.us`.

### Step 2: Wrestling with DNS Records
This was the first real hurdle. To make `ronam.us` point to GitHub's servers, I had to update the domain's "address book."

I logged into my Squarespace DNS settings and deleted all the default records. Then, I added five new custom records:
*   **One CNAME Record:** Host set to `www`, pointing to my GitHub URL (`rohitdas.github.io`).
*   **Four A Records:** Host set to `@` (the root domain), pointing to GitHub's four IP addresses (`185.199.108.153`, `185.199.109.153`, etc.).

**The Lesson Learned:** DNS propagation requires patience. When I checked GitHub immediately after, it threw a "DNS check failed" error. Furthermore, even when the check passed, visiting my site loaded an expired Squarespace placeholder. I realized my local ISP and browser had cached the old routing. Checking the site on my phone via cellular data (bypassing my home Wi-Fi) confirmed the connection was actually successful.

### Step 3: Applying a Professional Theme
Writing raw HTML for every blog post sounded like a nightmare. GitHub supports a few default themes, but I wanted something richer. I opted for a powerful third-party theme called **Minimal Mistakes**.

To install it, I created a `_config.yml` file in my repository's root directory. This is where I encountered my next major roadblock. 

I wrote my configuration file, but my site immediately crashed and failed to build. Why? Because .yml files use a strict spacing syntax called YAML. By fixing the indenting to follow the strict guidelines I was able to get the site built.

### Step 4: The Unstyled Page Glitch
Once the theme successfully built, I eagerly went to ronam.us only to find a completely unstyled, white page with plain blue text.
The HTML was there, but the CSS (the visual styling) was broken.
It turns out, this is a quirk of the SSL certificate process. GitHub was still working in the background to provision my secure HTTPS certificate. Because my _config.yml file strictly told the theme to fetch its styling over a secure https:// connection, my browser blocked it.
To fix this waited patiently until the **use HTTPS** checkbox was available on GitHub and selected that, which then fixed the issue.

### Step 5: Web-Optimizing Photos
When I started uploading photos for the homepage, I noticed they looked completely washed out and flat compared to how they looked on my phone.
I realized that my phone was capturing images in a wide color space with HDR, but standard web browsers are optimized for the narrower sRGB color space. When I cropped the photos on my device, it stripped that metadata, causing the web browser to render a dull image. The fix was simple: I convert them to sRGB before uploading them to the GitHub assets folder. I will need to find a scalable solution to this for future photo uploads.

### Step 6: Adding more content
Created separate markdown files for various pages I want on the website and the necessary folder structure to manage future posts. I tweaked the layout and text a few times. This post is the very first real post, but I look forward to expanding this over time.

### The Verdict
Building this site required a bit of troubleshooting, from bypassing local caches to debugging YAML indentation. But the result is a blazing-fast, secure, and beautifully themed website that costs absolutely nothing to host. Now, the infrastructure is out of the way, and Onam and I can focus entirely on logging our adventures.
