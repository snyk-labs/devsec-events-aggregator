# devsec-events-aggregator

This project aims to aggregate event data for various dev/sec events.


## Purpose

At [Snyk](https://snyk.io), we do a lot of events. We are a large developer security company and
try to participate in a number of developer/security events each year. Unfortunately, it's hard to
manage this at scale!

Some of the issues we've run into over time are things like:

- How can we figure out what events are coming up?
- How can we figure out what events are coming up in a particular region?
- How can we submit talks to an event's call-for-papers (CFP)?
- When does the event's CFP close?
- etc.

There are, thankfully, a lot of good event databases available. And while they're all different,
they make finding and analyzing events far simpler.

Here are some notable event databases in the developer/security space:

- https://github.com/scraly/developers-conferences-agenda
- https://infosec-conferences.com

To make it easier for us to analyze event opportunities at scale, we're building this project.

The goal of this project is to grab event data from existing event databases, clean it up, and
put it into a simplified JSON format that we can use for automated analysis.


## Event Schema

Below is our JSON schema that we use for aggregating events. This is the "end state" of what we
want an event to look like after aggregation and cleaup has been done.

```json
{
  "cfp": {
    "closes": "2024-06-30",
    "url": "https://forms.gle/ScdFFZQD6yPNFr9S8"
  },
  "ends": "2024-12-08",
  "location": {
    "city": "Amsterdam",
    "country": "NL"
  },
  "name": "Winter of C++",
  "starts": "2024-12-07",
  "url": "https://winterofcpp.vercel.app"
}
```

- `cfp` - JSON object or `null`. Includes CFP-related information.
  - `cfp.closes` - The date at which the CFP will be closed to new submissions.
  - `cfp.url` - **(required)** The URL of the website pointing to the CFP.
- `ends` - **(required)** The date at which the event will end.
- `location` - JSON object or `null`. Includes location-related information for events with
    a physical component.
  - `location.city` - The city the event is taking place in.
  - `location.country` - The country the event is taking place in. This is in [ISO 3166-1 Alpha-2 format](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2).
- `name` - **(required)** - The event name.
- `starts` - **(required)** - The date at which the event starts.
- `url` - **(required)** - The URL of the website pointing to the event.
