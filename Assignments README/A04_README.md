# Assignment 04 — IIoT Protocol Lab: Reflective Journal

**Course:** ITAI 3377  
**Group:** Brandy Griffin, Michael Garcia, Judith Barrios

---

## What This Was

This was the written reflection for Lab 04. It covers what each of us contributed, what the protocols actually felt like to work with, how we solved the errors we ran into, and where this kind of work could go in the future.

---

## My Role

Before we started coding I put together research notes on all three protocols — what each one is for, how it works, and when you'd choose it over the others. That helped us make better decisions during the build.

During testing I helped with OPC UA. When the script threw a `TypeError` on node operations I went through the asyncua documentation to find the correct async usage, which helped narrow down the fix.

On the writing side I drafted the learning outcomes section, reviewed the documentation for accuracy, and wrote the future applications part.

---

## What the Errors Taught Us

| Error | What caused it | How we fixed it |
|-------|---------------|-----------------|
| `RuntimeError: Calling Tcl from different apartment` | MQTT callback ran on a background thread, but Tkinter needs the main thread for GUI updates | Routed data through a thread-safe queue |
| Port 5683 already in use | Previous CoAP process still had the port after restart | Used `netstat -ano` to find the PID, then `taskkill /PID /F` |
| `TypeError` on OPC UA node operations | Missing `await` on async calls | Added `await` consistently based on asyncua docs |

Every protocol broke in a different way, and each fix required actually understanding what was happening under the hood. That was the most valuable part of the whole lab.

---

## Files

| File | Description |
|------|-------------|
| `A04_Judith_Barrios_ITAI_3377.docx` | Full group reflective journal |
