<img src="assets/logo.png" width="112" height="112" alt="Starling logo">

# Starling

Estimate resource capacity and actual occupied time from a booking schedule. This Blyx workflow framework is part of the calendar, scheduling and local time collection.

Summing all booking durations double-counts overlap. Measure occupied time separately from peak resource demand. [PostgreSQL, range types](https://www.postgresql.org/docs/current/rangetypes.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-starling.git
cd blyx-starling
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-starling) · [Package page](https://www.blyx-lang.space/packages/starling) · [Handbook](https://doc.blyx-lang.space/guide/starling)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-starling.git vendor/starling
```

```blyx
use vendor::starling::starling;

fn main() {
    let starts = [0, 2, 4];
    let ends = [4, 5, 7];
    let capacity = 1.0;
    let result = starling_capacity(starts, ends, capacity);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
7
2
2
1
```

## API

`starling_capacity(starts, ends, capacity)`

Returns [covered ticks, peak simultaneous bookings, earliest peak, capacity shortfall]. Starts must be sorted; adjacent bookings can share a resource. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| starts | Vector of values, each a exact signed integer |
| ends | Vector of values, each a exact signed integer |
| capacity | A positive exact integer |

## Run the command-line project

Run the example with your own numbers. Vector arguments accept up to 16 comma-separated entries; use `[]` for an empty vector. The imported API accepts longer vectors. Invalid arguments return a nonzero exit status.

```sh
blyxc native-run project.blyx -- "0,2,4" "4,5,7" 1
```

## Libraries

- [IntervalUnion](https://github.com/Rahulchaube1/blyx-intervalunion/tree/v0.1.0) — Measure union length and coverage components of sorted half-open intervals.
- [PeakSlots](https://github.com/Rahulchaube1/blyx-peakslots/tree/v0.1.0) — Find peak simultaneous occupancy of half-open intervals.

This release includes identical copies of both library modules so a tagged clone can build offline.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-starling/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
