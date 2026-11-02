# Structure from DBB

Structure from DBB proposes and checks the main hull structure of a ship from its Design Building Block (DBB) arrangement. Open a design saved by the [Ship Design Building Block Editor](https://shiplab.github.io/dbb/) and the app gives, region by region:

- **Longitudinal structure:** plates, longitudinals and primary members sized to DNV Rules for Ships Pt.3 Ch.2 (January 2015, ships under 100 m), with the hull girder section modulus checked against the rule value along the length.
- **Transverse framing where it fits:** guessed per region (small ships and the ends), with floors, side frames, deck beams and their end brackets.
- **Buckling and hull girder shear:** plates and longitudinals under hull girder compression, and the shear stress at the neutral axis, in simplified form.
- **Transverse web frame:** a beam model of the frame in the manner of the 3D Beam program of Nauticus Hull, with Timoshenko beams. Load cases are read from the blocks (full load, ballast, tank test) and can be edited. The girders are sized from the computed forces.
- **Transverse bulkheads:** found in the arrangement and sized with a simplified Sec.9 method.
- **Learn the basics:** eight short lessons on a box barge (loads, section properties, stresses, rule moments, local strength, buckling, a web frame member, holes and two-way loading), worked by hand and checked by the app, after the compendium of Sollied (2009).

Every value can be changed by hand and is checked again at once. A 3D view shows the structure on the real hull. *Report PDF* writes a report of the whole ship, and *Save work* keeps your changes in a .json file.

Version 1.0.0, November 2026. User manual: [docs/manual.pdf](docs/manual.pdf) (text also in [docs/manual.md](docs/manual.md)).

**For educational use only.** See the disclaimer under Limits.

## Run it

On the web: this folder is a static site. On GitHub, push it to a repository and turn on *Settings → Pages → Deploy from a branch* (main, root); the app is then at `https://<user>.github.io/<repository>/`. The empty `.nojekyll` file makes Pages serve the files as they are.

On your computer: open `index.html` in a browser. It needs no internet: Three.js and the fonts are in `vendor/`. Some browsers limit pages opened from a file; if so, serve the folder, for example with `python -m http.server`, and open `http://localhost:8000`.

## Use it

1. Press *Open DBB file* and choose a design saved by the DBB editor (one hull). Or pick an example: the barge of the compendium (opened at start), R/V Gunnerus, PSV, AHTS, tanker, feeder container ship or handysize bulk carrier.
2. Pick a region in the side view or the list.
3. Switch between *Section*, *3D* and *Frame*. In Frame, choose a load case and tick *Spaces* and *Loads*.
4. Change thicknesses, profiles, girders and load cases in the tabs under the drawing.
5. *Report PDF* for the report, *Save work* to keep your work.
6. *Learn* opens the lessons on the barge.

*How to* in the app explains each step. The [user manual](docs/manual.pdf) covers the method, the assumptions and the limitations, with exercises for students.

## Limits

- Made for teaching and early concept exploration.
- One section and one web frame per region.
- Buckling (no lateral-torsional buckling), transverse frames, brackets and hull girder shear are simplified estimates.
- No fatigue, finite element analysis or torsion.
- The web frame is a symmetric half model with no accelerations of the tank contents.
- The 2015 rules are for ships under 100 m; above that the results are indicative only.
- For educational use only. Structure from DBB is made for teaching and early concept exploration. Its results are simplified estimates; they must not be used for the design, approval or construction of any ship, for class or flag-state documentation, or for any safety-critical decision. Provided as it is, without warranty of any kind; the authors accept no liability for its use.

## Browsers

Current Chrome, Edge, Firefox and Safari. The 3D view needs WebGL. The page follows the light or dark setting of your system.

## Files

- `index.html`: the app, one file, with the DBB core, the examples and the lessons inside.
- `docs/manual.pdf`: the user manual.
- `vendor/three.min.js`, `vendor/OrbitControls.js`: [Three.js](https://threejs.org/) r147, MIT license.
- `vendor/fonts/`: Barlow, Barlow Condensed and IBM Plex Mono (latin subsets from Fontsource), SIL Open Font License 1.1.
- `CHANGELOG.md`: what is in each version. `LICENSE`: MIT.

The source (modules, tests, manual build) is kept apart from this published folder.

## License

MIT, see [LICENSE](LICENSE). The R/V Gunnerus example data stays under CC BY-NC 4.0, the cover of the Sollied compendium is used with his permission, and Three.js and the fonts in `vendor/` keep their own licenses.

## Credits and citing

Developed by Henrique Gaspar, NTNU, 2026. The lessons under Learn are inspired by the compendium Strukturdesign av skip by Arne Jan Sollied. It builds on the Hull Scantlings Design Assistant made in 2018 by Olivia Chaves in her master thesis at NTNU, supervised by Henrique Gaspar and Henning Borgen.

The R/V Gunnerus example uses the open Gunnerus data (shiplab/gunnerus, CC BY-NC 4.0, courtesy of Polarkonsult and NTNU). That example data stays under CC BY-NC 4.0. The other examples are the illustrative designs of the DBB editor.

References:

- Chaves, O.S., Gaspar, H.M. and Borgen, H. (2018). An Open and Collaborative Knowledge-Based Approach for Automated Design of Hull Scantlings. ICSOS 2018, Gothenburg.
- Chaves, O.S. (2018). A Knowledge-Based Approach for Automated Design of Hull Scantlings. Master thesis, NTNU.
- Gaspar, H.M., Fonseca, Í.A. and Andrews, D. (2024). Wither now the Design Building Block (DBB) Approach. IMDC 2024. https://doi.org/10.59490/imdc.2024.915
- DNV (2015). Rules for Classification of Ships, Pt.3 Ch.2, Hull Structural Design, Ships with Length less than 100 metres.
- DNV (2009). Nauticus Hull User Manual, 3D Beam, program version 11.0.
- Sollied, A.J. (2009). Strukturdesign av skip (compendium). Høgskolen i Ålesund.
