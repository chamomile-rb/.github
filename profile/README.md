<div align="center">

# 🌼 Chamomile

**Build terminal apps in pure Ruby.**

A reactive TUI framework inspired by [Bubbletea](https://github.com/charmbracelet/bubbletea), bringing the Elm Architecture to your terminal.

[Website](https://chamomile-rb.github.io) · [API Docs](https://chamomile-rb.github.io/docs/chamomile/) · [Get Started](#get-started)

</div>

---

## The Ecosystem

<table>
<tr>
<td width="50%" valign="top">

### 🌼 [Chamomile](https://github.com/chamomile-rb/chamomile) — Core Framework

The engine. An Elm Architecture event loop with async commands, signal handling, diff rendering, mouse support, and full terminal control.

```ruby
gem install chamomile
```

- **Model / Update / View** — your class is the app
- **Thread pool commands** — async by default
- **FPS-throttled diff renderer** — only redraws what changed
- **Mouse, paste, focus, resize** events
- **Cooperative cancellation & streaming**

</td>
<td width="50%" valign="top">

### 🌸 [Petals](https://github.com/chamomile-rb/petals) — Components

13 reusable TUI components that follow the same `update`/`view` protocol. Drop in and go.

```ruby
gem install petals
```

- **TextInput** & **TextArea** — full editing, paste, echo modes
- **Viewport** — scrollable content with keyboard & mouse
- **Table** & **List** — data display with filtering & pagination
- **Spinner**, **Progress**, **Timer**, **Stopwatch**
- **FilePicker**, **Paginator**, **Cursor**, **Help**

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🎨 [Flourish](https://github.com/chamomile-rb/flourish) — Styling

CSS-like box model for the terminal. Colors, borders, padding, alignment, and layout composition. Zero dependencies.

```ruby
gem install flourish
```

- **True color**, ANSI 256, basic ANSI
- **10 border presets** with per-side colors
- **Padding, margin, width, alignment**
- **Horizontal/vertical join & place**

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

class Hello
  include Chamomile::Model
  include Chamomile::Commands

  def update(msg)
    case msg
    when Chamomile::KeyMsg
      return quit if msg.key == "q"
    end
    nil
  end

  def view
    "Hello from Chamomile!\n\nPress q to quit."
  end
end

Chamomile.run(Hello.new)
```

<div align="center">

### How It Works

**Model** → Your class holds state&ensp;·&ensp;**Update** → Receives messages, returns commands&ensp;·&ensp;**View** → Returns a string to render

Everything is a command. Async by default, composable by design.

---

<sub>MIT License</sub>

</div>
