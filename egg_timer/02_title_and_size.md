---
layout: default
title: Chapter 2 - Title
nav_order: 2
parent: Egg timer
has_children: false
---

# Chapter 2 - Title and size

## Goals

The intent of this section is to set a custom title and the size of the window.

![Window with custom title and set size](02_title_and_size.png)

## Outline

This code is very similar to that of [chapter 1](01_empty_window.md). We add:

- one more import
- two parameters when calling `app.NewWindow()`

## Code

```go
package main

import (
	"gioui.org/app"
	"gioui.org/unit"
)

func main() {
  go func() {
	// create new window
	w := app.NewWindow(
		app.Title("Egg timer"),
		app.Size(unit.Dp(400), unit.Dp(600)),
	)

	// listen for events in the window.
	for range w.Events() {
	}
  }()
app.Main()
}
```

## Comments

[gioui.org/unit](https://pkg.go.dev/gioui.org/unit) implements device independent units and values. The docs describe a handful of alternatives:

| Type | Description                                                     |
| :--: | :-------------------------------------------------------------- |
|  dp  | Device independent pixel - independent of the underlying device |
|  sp  | Scaled pixel - used for text sizes                              |
|  px  | Pixels - used for precision for the actual device               |

In general, `dp` is the most widely used; we like to keep device independency when we can. Hence that's what we use when we define the window size inside `app.NewWindow()`.

The [options](https://pkg.go.dev/gioui.org/app#Option) of `app.NewWindow()` are fairly self-explanatory, but take note of a few things:

- The size is set using `app.Size(x, y)`.
- The window can be freely resized. Try it! If you want to limit the size you can add:
  - MaxSize
  - MinSize
  - Or use both, effectively locking the window size
- A fullscreen option is available if needed.
- If you're building for Android, Status and Navigation colors can be set here.

---

[Next chapter](03_button.md){: .btn .fs-5 .mb-4 .mb-md-0 }
