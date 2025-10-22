# Naive workflow

Writing hardware acceleration is hard. So we want to start with some intuitive
and naive workflow.

1. Quantization: Web Safe Colors
2. Dithering: no dithering

## Quantization: Web Safe Colors

Many CPU quantization algorithms does not work well on GPU.

Start with simple quantize colors into 216 fixed [web safe colors][wsc].

[wsc]: https://en.wikipedia.org/wiki/Web_colors#Web-safe_colors#Web-safe_colors

$$
R' = R / 51 \\
G' = G / 51 \\
B' = B / 51 \\
Idx = 36 * R' + 6 * G' + B' + 1
$$

Index `0` is reserved for transparency.

## Storage

Made a `W * H * 216 / 6 / 4` buffer.

XXX: too much vram consumed
