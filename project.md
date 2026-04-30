# Tmr
(timer, too lazy for vowels)

Basic timer that I can start and stop.
Can have multiple running, stretch goal.
Saves durations to... db?
Then can run a report.

Toggl like, but simpler.

... hang on, why not `timewarrior` !?

## Stack
- Golang
- SQLite built-in

## Commands
- `start` starts a timer, args: project, task
- `stop` stops a running timer
- `update` update the start, end time, or duration of a timer, can be running
- `list` list durations
- `print` print running timers
- `export` export a particular timer

## Examples
```sh
# start a unnamed timer
tmr start

# start a named timer
tmr --name work start

# stop all timers

# stop last time
```

## MVP
- one timer running at once
- local machine only for now
