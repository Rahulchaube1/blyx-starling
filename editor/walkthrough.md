## Size a resource pool from overlapping bookings

Returns [covered ticks, peak simultaneous bookings, earliest peak, capacity shortfall]. Starts must be sorted; adjacent bookings can share a resource. Invalid arguments and nonfinite results return an empty vector.

1. Open an empty file named `starling-demo.blyx`.
2. Type `blyx-starling-demo` and select **Starling — runnable example**. You can also use **Snippets: Fill File with Snippet**.
3. Choose **Blyx: Run File** from the command palette. Change an argument near the end of `fn main()` to try another input.

Expected output

```text
7
2
2
1
```

[Work through the example in the browser](https://www.blyx-lang.space/play?example=package-starling)
