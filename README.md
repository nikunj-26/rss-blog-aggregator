# Gator

A small, terminal-based RSS feed aggregator written in Go.

Gator lets you create users, subscribe to RSS feeds, collect posts, and browse
your personalized feed from the command line.

## Requirements

- Go 1.27+
- PostgreSQL
- A database created for Gator

## Setup

1. Apply the migrations in [`sql/schema`](./sql/schema) to your PostgreSQL
   database.
2. Create `~/.gatorconfig.json`:

   ```json
   {
     "db_url": "postgres://user:password@localhost:5432/gator?sslmode=disable"
   }
   ```

3. Run the CLI:

   ```bash
   go run . register alice
   ```

## Commands

```text
register <name>       Create a user and log in
login <name>          Switch users
users                 List users
addfeed <name> <url>  Add and follow an RSS feed
feeds                 List all feeds
follow <url>          Follow a feed
unfollow <url>        Unfollow a feed
following             List your followed feeds
agg <duration>        Collect feeds continuously (for example, 1m)
browser [limit]       Browse collected posts
reset                 Remove application data
```

For example:

```bash
go run . addfeed "Go Blog" https://go.dev/blog/feed.atom
go run . agg 1m
go run . browser 10
```

Stop the aggregator with `Ctrl-C`.
