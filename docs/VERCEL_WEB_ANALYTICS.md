# Vercel Web Analytics Setup Guide

This guide explains how Vercel Web Analytics has been implemented in the Seraph project.

## Overview

Vercel Web Analytics provides insights into your website's performance and user behavior. This project has been configured to automatically track visitor data and page views when deployed on Vercel.

## Implementation Details

### What's Been Set Up

Vercel Web Analytics has been enabled for this static HTML site using the plain HTML implementation approach, as documented in the [Vercel Web Analytics documentation](https://vercel.com/docs/analytics).

### Integration Points

The Vercel Web Analytics script has been added to all main HTML pages:
- `index.html` - Main homepage
- `404.html` - 404 error page
- `host.html` - Hosting/deployment information page
- `offline.html` - Offline mode page
- `settings.html` - Settings page
- `updatelog.html` - Update log page

### Script Implementation

For plain HTML sites, the following scripts have been added to the `<head>` section of each HTML file:

```html
<script>
  window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };
</script>
<script defer src="/_vercel/insights/script.js"></script>
```

The first script initializes the Vercel Analytics API, while the second script loads the analytics tracking functionality asynchronously.

## How It Works

1. **Automatic Tracking**: Once deployed to Vercel, the analytics script automatically begins tracking:
   - Page views
   - Core Web Vitals (Largest Contentful Paint, First Input Delay, Cumulative Layout Shift)
   - Route information

2. **No Additional Configuration**: Since this is a static HTML site, no additional package installation or configuration is required beyond adding the script tags.

3. **Privacy Compliant**: Vercel Web Analytics is designed to respect user privacy and comply with various data protection standards.

## Deployment Requirements

To activate Vercel Web Analytics for this project:

### Prerequisites

1. **Vercel Account**: You'll need a [Vercel account](https://vercel.com/signup) (free tier available)
2. **Vercel Project**: [Create a new project](https://vercel.com/new) or connect an existing one

### Enabling Analytics on Vercel

1. Navigate to the [Vercel Dashboard](https://vercel.com/dashboard)
2. Select your project (Seraph)
3. Click the **Analytics** tab
4. Click **Enable** in the dialog that appears

> **Note**: Enabling Web Analytics will add new routes (scoped at `/_vercel/insights/*`) after your next deployment.

### Deploy Your Application

Deploy your application using one of these methods:

**Using Vercel CLI:**
```bash
vercel deploy
```

**Using Git Integration:**
We recommend [connecting your project's Git repository](https://vercel.com/docs/git#deploying-a-git-repository) to Vercel, which enables automatic deployments of your latest commits to main.

## Viewing Your Analytics Data

Once deployed:

1. Wait a few moments for data to be collected
2. Navigate to your [Vercel Dashboard](https://vercel.com/dashboard)
3. Select your project
4. Click the **Analytics** tab
5. Explore your data by viewing and filtering panels

### What You'll See

- **Page Views**: Track which pages are most popular
- **Core Web Vitals**: Monitor performance metrics
- **Top Pages**: See your most visited pages
- **Traffic Sources**: Understand where your visitors come from

After a few days of visitors, you'll be able to start exploring your data in more detail.

## Advanced Features

### Custom Events (Pro/Enterprise Plans)

Users on Pro and Enterprise plans can add custom events to track:
- Button clicks
- Form submissions
- Purchases
- Other user interactions

### Data Filtering

Vercel Web Analytics supports filtering data by:
- Time range
- Device type
- Country
- Browser
- Other dimensions

## Browser Requirements

You should be able to see a Fetch/XHR request in your browser's Network tab from `/_vercel/insights/view` when you visit any page. This indicates the analytics script is working correctly.

## Privacy and Compliance

Vercel Web Analytics is designed to:
- Respect user privacy
- Comply with GDPR, CCPA, and other data protection regulations
- Use first-party analytics (no third-party cookies)

For more information, see [Vercel's Privacy Policy for Web Analytics](https://vercel.com/docs/analytics/privacy-policy).

## Troubleshooting

### Analytics Not Showing Data

1. **Verify Deployment**: Ensure your project is deployed on Vercel
2. **Check Network Tab**: Look for `/_vercel/insights/script.js` and `/_vercel/insights/view` requests
3. **Wait for Data**: Analytics may take a few minutes to appear
4. **Check Enablement**: Verify analytics is enabled in your Vercel project settings

### Missing Script Tags

If analytics isn't working:
1. Verify the script tags are present in your HTML files
2. Check browser console for errors
3. Ensure you're visiting the deployed version (not localhost)

## Useful Resources

- [Vercel Web Analytics Documentation](https://vercel.com/docs/analytics)
- [Vercel Analytics API Reference](https://vercel.com/docs/analytics/package)
- [Custom Events Guide](https://vercel.com/docs/analytics/custom-events)
- [Analytics Filtering Guide](https://vercel.com/docs/analytics/filtering)
- [Privacy and Compliance](https://vercel.com/docs/analytics/privacy-policy)
- [Limits and Pricing](https://vercel.com/docs/analytics/limits-and-pricing)
- [Troubleshooting Guide](https://vercel.com/docs/analytics/troubleshooting)

## Next Steps

1. **Enable Analytics**: Follow the deployment requirements above
2. **Deploy Your Code**: Use `vercel deploy` or Git integration
3. **Monitor Your Data**: Check the Analytics dashboard after deployment
4. **Optimize**: Use insights to improve your site's performance and user experience
