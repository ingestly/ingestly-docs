# Sample Queries

- In these samples, a table name of the log is `ingestly.logs`

## Standard Metrics

### Pageviews
`select count(*) from ingestly.logs where action='view' and category='page';`

### Visits
- Not supported (still using it?? let me know your use-cases.)

### Unique Visitors
`select count(distinct ingestly_id) from ingestly.logs;`
