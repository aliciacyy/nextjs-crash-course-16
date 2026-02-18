# PostHog post-wizard report

The wizard has completed a deep integration of your Next.js App Router project. PostHog has been configured with client-side analytics using the modern `instrumentation-client.ts` approach for Next.js 15.3+. A reverse proxy has been set up through Next.js rewrites to improve tracking reliability and bypass ad blockers. Three custom events have been instrumented to track key user interactions across the application.

## Integration Summary

| File | Changes |
|------|---------|
| `instrumentation-client.ts` | Created - Initializes PostHog SDK with reverse proxy, error tracking, and debug mode |
| `next.config.ts` | Modified - Added rewrites for PostHog reverse proxy and trailing slash support |
| `.env.local` | Created - Contains PostHog API key and host environment variables |
| `components/ExploreBtn.tsx` | Modified - Added `explore_events_clicked` event capture |
| `components/EventCard.tsx` | Modified - Added `event_card_clicked` event capture with event properties |
| `components/NavBar.tsx` | Modified - Added `nav_link_clicked` event capture with link name property |

## Events Instrumented

| Event Name | Description | File |
|------------|-------------|------|
| `explore_events_clicked` | User clicked the 'Explore events' button on the homepage to scroll to the events section | `components/ExploreBtn.tsx` |
| `event_card_clicked` | User clicked on an event card to view event details (includes event_title, event_slug, event_location, event_date properties) | `components/EventCard.tsx` |
| `nav_link_clicked` | User clicked a navigation link (includes link_name property: logo, home, events, create_event) | `components/NavBar.tsx` |

## Next steps

We've built some insights and a dashboard for you to keep an eye on user behavior, based on the events we just instrumented:

### Dashboard
- [Analytics basics](https://us.posthog.com/project/316836/dashboard/1288078) - Main dashboard with all insights

### Insights
- [Explore Events Button Clicks](https://us.posthog.com/project/316836/insights/6AgybX9i) - Tracks homepage explore button engagement
- [Event Card Clicks](https://us.posthog.com/project/316836/insights/up36YLe4) - Tracks event card interactions
- [Navigation Link Clicks](https://us.posthog.com/project/316836/insights/sIP2lYBw) - Tracks navigation usage by link name
- [Event Discovery Funnel](https://us.posthog.com/project/316836/insights/3gMA8QoX) - Conversion funnel from page view to event selection
- [Popular Events by Clicks](https://us.posthog.com/project/316836/insights/JMeGVKfQ) - Shows which events are most popular

## Configuration Details

- **API Key**: Stored in `.env.local` as `NEXT_PUBLIC_POSTHOG_KEY`
- **Host**: Stored in `.env.local` as `NEXT_PUBLIC_POSTHOG_HOST`
- **Reverse Proxy**: Configured via `/ingest` route in `next.config.ts`
- **Error Tracking**: Enabled via `capture_exceptions: true`
- **Debug Mode**: Enabled in development environment

### Agent skill

We've left an agent skill folder in your project at `.claude/skills/posthog-integration-nextjs-app-router/`. You can use this context for further agent development when using Claude Code. This will help ensure the model provides the most up-to-date approaches for integrating PostHog.
