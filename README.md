# @weldable/integration-google-calendar

Google Calendar event actions for Weldable.

Part of the [Weldable](https://weldable.ai/) integration library — see [@weldable/integration-core](https://github.com/weldable/integration-core) for the full catalog.

## Install

```bash
npm install @weldable/integration-google-calendar @weldable/integration-core
```

`@weldable/integration-core` is a peer dependency and must be installed alongside this package.

## Usage

```ts
import integration from '@weldable/integration-google-calendar'

// List upcoming events
const list = integration.actions.find(a => a.id === 'google_calendar.list_events')!

const events = await list.execute(
  {
    calendarId: 'primary',
    timeMin: new Date().toISOString(),
    maxResults: 5,
  },
  ctx, // ActionContext from your Weldable-compatible host
)

// Create an event
const create = integration.actions.find(a => a.id === 'google_calendar.create_event')!

await create.execute(
  {
    calendarId: 'primary',
    summary: 'Sprint planning',
    start: { dateTime: '2025-02-03T10:00:00-08:00' },
    end: { dateTime: '2025-02-03T11:00:00-08:00' },
  },
  ctx,
)
```

## Contributing and releasing

See [CONTRIBUTING.md](https://github.com/weldable/integration-core/blob/main/CONTRIBUTING.md) in `@weldable/integration-core` for the development workflow and release process.

## License

MIT
