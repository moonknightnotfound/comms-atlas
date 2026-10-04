# Communication Systems

Communication systems are how information is carried from a source to a destination over a channel such as air, cable, or fibre. A transmitter shapes the data into a signal, the channel carries it (adding noise and distortion), and a receiver recovers the original data.

This guide takes you from the basics of how signals are carried, through how errors are detected, to building a working radio chain in software.

## Basics of Communication Systems

Every link, wired or wireless, follows the same chain:

1. **Source:** produces the information (voice, sensor data, bits).
2. **Modulation:** imprints the information onto a carrier signal suited to the channel.
3. **Channel:** carries the signal and corrupts it with noise, interference, and attenuation.
4. **Demodulation and error checking:** recovers the bits and detects whether they arrived intact.

The goal is to deliver data reliably, within the bandwidth and power available.

## How to Use This Guide

Theory tells you why a link works. Once the concepts are clear, tools like GNU Radio make sense because the blocks on screen map to ideas you already know, instead of being wired together by guesswork.

Develop consistent learning habits:

- **Learn and apply:** Study one concept, then sketch or simulate a small example before moving on.
- **Understand your errors:** When a flowgraph or calculation fails, revisit the relevant theory before searching for fixes.
- **Focus on understanding:** Do not rush. Re-read, re-watch, or work through a numeric example until the idea is clear.

---

# Stage 1: Foundations (Beginner)

**Intro video:**
[https://www.youtube.com/watch?v=IyGwvGzrqp8](https://www.youtube.com/watch?v=IyGwvGzrqp8)

Start here to get the overall picture of how a communication link fits together before reading the detail-heavy articles below.

**Radio frequency spectrum bands, GeeksforGeeks:**
[https://www.geeksforgeeks.org/electronics-engineering/bands-in-radio-frequency-spectrum/](https://www.geeksforgeeks.org/electronics-engineering/bands-in-radio-frequency-spectrum/)

The spectrum is divided into bands from very low to extremely high frequency. This article tabulates each band's frequency range, propagation behaviour, and typical applications. It is the reference for why a given system uses the frequency it does.

> **How to approach this stage**
>
> Watch the intro video once straight through, then again with notes.
>
> Memorise the order of the bands (VLF to EHF) and one real application for each.
>
> Do not try to memorise every frequency boundary, know the rough decades.
>
> Checkpoint: name the band for FM radio, Wi-Fi, GPS, and AM radio without looking.

---

# Stage 2: Modulation (Intermediate)

Modulation is the process of varying a property of a high-frequency carrier (amplitude, frequency, or phase) according to the message signal, so the message can travel efficiently over a channel.

**What is Modulation, GeeksforGeeks:**
[https://www.geeksforgeeks.org/computer-networks/what-is-modulation/](https://www.geeksforgeeks.org/computer-networks/what-is-modulation/)

The article covers Amplitude Modulation (AM), Frequency Modulation (FM), Phase Modulation (PM), Polarisation Modulation, Pulse-Code Modulation (PCM), and Quadrature Amplitude Modulation (QAM), and explains which carrier property each one varies.

> **How to approach this stage**
>
> Start with AM, FM, and PM, they are the core of everything else.
>
> For each type, draw the message, the carrier, and the modulated output by hand.
>
> Compare them: which resists noise best, which uses the least bandwidth, which is simplest to build.
>
> Checkpoint: explain from memory how QAM combines amplitude and phase to carry more bits per symbol.

---

# Stage 3: Error Detection (Intermediate)

Real channels flip bits. Error detection adds redundancy so the receiver can tell whether the data arrived intact.

**Checksum vs CRC, GeeksforGeeks:**
[https://www.geeksforgeeks.org/computer-networks/difference-between-checksum-and-crc/](https://www.geeksforgeeks.org/computer-networks/difference-between-checksum-and-crc/)

A checksum works by simple addition of the data, so it is cheap but misses some error patterns. A CRC uses polynomial division to produce a much stronger check value. The article compares their advantages, disadvantages, and use cases.

> **How to approach this stage**
>
> Compute a simple checksum by hand on a short byte sequence, then deliberately corrupt it and see what slips through.
>
> Work one CRC polynomial-division example on paper (binary long division with XOR).
>
> Checkpoint: write a small program that computes both a checksum and a CRC-8 and show a corruption that the checksum misses but the CRC catches.

---

# Stage 4: Hands-on with GNU Radio (Advanced)

GNU Radio is an open-source toolkit for building software-defined radio systems by connecting signal-processing blocks in a flowgraph. It brings modulation, filtering, and demodulation together in one working chain.

**GNU Radio tutorial:**
[https://www.youtube.com/watch?v=ufxBX_uNCa0](https://www.youtube.com/watch?v=ufxBX_uNCa0)

> **How to approach this stage**
>
> Follow the tutorial in GNU Radio Companion as you watch, pause and build each step yourself.
>
> Start with a signal source feeding a sink to see a sine wave, before adding any modulation.
>
> Reuse what you learned in Stage 2: build an AM or FM modulator and demodulator and compare the output with your hand-drawn waveforms.
>
> Checkpoint: a working flowgraph that modulates a tone, demodulates it, and shows matching input and output in the time sink.

---

# Recommended Tasks

- **Easy:** produce a one-page table of all RF bands with frequency range and one application each.
- **Medium:** hand-draw AM, FM, and PM for the same message signal, and implement a checksum and CRC-8 in code.
- **Hard:** build an end-to-end modulate and demodulate flowgraph in GNU Radio and add an error check on the recovered bits.

---

# Resource Index

| Stage | Level | Resource | Type |
|-------|-------|----------|------|
| 1 | Beginner | [Intro video](https://www.youtube.com/watch?v=IyGwvGzrqp8) | Video |
| 1 | Beginner | [Bands in the RF spectrum](https://www.geeksforgeeks.org/electronics-engineering/bands-in-radio-frequency-spectrum/) | Article |
| 2 | Intermediate | [What is Modulation](https://www.geeksforgeeks.org/computer-networks/what-is-modulation/) | Article |
| 3 | Intermediate | [Checksum vs CRC](https://www.geeksforgeeks.org/computer-networks/difference-between-checksum-and-crc/) | Article |
| 4 | Advanced | [GNU Radio tutorial](https://www.youtube.com/watch?v=ufxBX_uNCa0) | Video |
