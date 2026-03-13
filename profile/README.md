<div align="center">

# 🌼 Chamomile

**Build terminal apps in pure Ruby.**

An event-driven TUI framework with declarative callbacks, a composable View DSL, terminal styling, reusable components, and zero runtime dependencies.

[Website](https://chamomile-rb.github.io) · [API Docs](https://chamomile-rb.github.io/docs/chamomile/) · [Get Started](#get-started)

</div>

---

## What's Inside

<table>
<tr>
<td width="50%" valign="top">

### 🌼 [Chamomile](https://github.com/chamomile-rb/chamomile) — The Complete Ruby TUI Framework

One gem. Everything you need for terminal UIs in Ruby.

```ruby
gem install chamomile
```

**Core Runtime**
- **View DSL** — `panel`, `text`, `list`, `table`, `status_bar`
- **Declarative callbacks** — `on_key`, `on_mouse`, `on_tick`
- **Thread pool commands** — async by default
- **FPS-throttled diff renderer** — only redraws what changed
- **Mouse, paste, focus, resize** events

**Styling** — CSS-like box model with true color, 10 border presets, padding, margin, alignment, horizontal/vertical layout composition

**Components** — 13 reusable TUI components: TextInput, TextArea, Viewport, Table, List, FilePicker, Spinner, Progress, Timer, Stopwatch, Paginator, Cursor, Help

</td>
<td width="50%" valign="top">

### 🚂 [Lazyrails](https://github.com/chamomile-rb/lazyrails) — Flagship App

A lazygit-style TUI for Rails developers. Routes, migrations, models, tests, server, gems — all in one split-pane interface.

```ruby
gem install lazyrails-tui
```

- **13+ navigable panels** — status, routes, models, DB, tests…
- **Live server log streaming** with auto-detection
- **Command log with undo** — reverse generators & migrations
- **Smart introspection** via Rails APIs, not text parsing

</td>
</tr>
</table>

---

## Get Started

```ruby
require "chamomile"

class Counter
  include Chamomile::Application

  def initialize
    @count = 0
  end

  on_key(:up, "k")   { @count += 1 }
  on_key(:down, "j") { @count -= 1 }
  on_key("r")        { @count = 0 }
  on_key("q")        { quit }

  def view
    panel(title: "Counter", border: :rounded, color: "#7d56f4") do
      text "Count: #{@count}", bold: true, color: "#7d56f4"
      text ""
      status_bar "↑/k increment · ↓/j decrement · r reset · q quit"
    end
  end
end

Chamomile.run(Counter.new)
```

<div align="center">

### How It Works

**Application** → Your class is the app&ensp;·&ensp;**Events** → Declare callbacks with `on_key`, `on_mouse`, `on_tick`&ensp;·&ensp;**View DSL** → Build layouts with `panel`, `text`, `list`, `table`

Everything is a command. Async by default, composable by design.

---

<sub>MIT License</sub>

</div>
