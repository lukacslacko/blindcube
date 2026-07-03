# blindrubik

Single-page web app: paste a 3×3 Rubik's cube scramble and get the **Speffz
letter sequences** to memorize for a blindfolded solve.

**Live:** https://lukacslacko.github.io/blindrubik/

## Features

- Old Pochmann style tracing with alphabetical break-ins; letters chunked in
  pairs, cycle structure shown separately.
- Buffer choices: edges UR / UF / DF (Old Pochmann, 3-style, M2), corners
  UBL / UFR.
- Parity detection, notes for pieces misoriented in place, and a warning when
  the buffer piece itself is twisted/flipped in place.
- Cube net view of the scrambled state with Speffz letters on every position
  and the buffers highlighted — doubles as a lettering reference.

## Implementation

Everything lives in a single dependency-free `index.html`. Move permutations
are generated at load time from 3D sticker coordinates (each face turn is a
−90° rotation of the layer's stickers, matched back to facelets) rather than
hand-typed tables. Tracing follows the piece currently in the buffer to the
position where its reference sticker belongs, emitting Speffz letters; new
cycles break in at the alphabetically first unsolved letter and close on their
starting piece, so flips/twists in place appear as 2-target break-ins.

Sanity checks used during development: every move permutation has order 4,
scramble `R` with Old Pochmann buffers reproduces the textbook memo
(edges `JVT`, corners `BJVTB`), and edge/corner target-count parity agrees
across random scrambles for all buffer combinations.

## License

MIT — see [LICENSE](LICENSE).
