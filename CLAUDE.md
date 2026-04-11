# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Tmr is a local CLI timer tool written in Go with SQLite storage. It tracks time against project+task labels and supports basic reporting. Think Toggl, but simpler and offline.

## Commands

```bash
go build ./...          # build
go run .                # run without building
go test ./...           # run all tests
go test ./internal/...  # run tests for a specific package
go test -run TestName   # run a single test by name
```

## Architecture

The app is a Go CLI (planned with [cobra](https://github.com/spf13/cobra) or similar) backed by a local SQLite database.

Key layers:
- **cmd/** — CLI command definitions (`start`, `stop`, `update`, `list`, `print`)
- **internal/db/** — SQLite access layer (schema, queries, migrations)
- **internal/timer/** — timer domain logic (start/stop state, duration calculation)

### Data model

A **duration** is the core record: a start time, optional end time, project label, and task label. A timer is "running" when it has a start time but no end time. MVP enforces only one running timer at a time.

### CLI commands

| Command  | Purpose                               |
|----------|---------------------------------------|
| `start`  | Begin a new timer (args: project, task) |
| `stop`   | Stop the currently running timer       |
| `update` | Edit start/end time of a recent entry  |
| `list`   | List recorded durations                |
| `print`  | Show currently running timers          |
