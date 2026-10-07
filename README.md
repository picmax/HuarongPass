# 华容道 · Huarong Pass — Sliding Block Puzzle

A complete, self-contained HTML version of **Huarong Dao (华容道)** — the classic Chinese sliding-block puzzle known in the West as **Klotski**. Slide the warlord Cao Cao out of the pass.

**▶ Play it here:** https://picmax.github.io/HuarongPass/  
*(enable GitHub Pages: Settings → Pages → Deploy from a branch → `main` / root, then replace the URL above)*

No build step, no dependencies — a single `index.html` file that runs in any modern browser, desktop or mobile.

---

## The Story

In 208 AD, at the Battle of Red Cliffs (赤壁), the Wei warlord **Cao Cao** was crushed by the allied forces of Sun Quan and Liu Bei. Fleeing west through the narrow **Huarong Pass (华容道)**, he was met by the Shu commander **Guan Yu** — who, remembering an old debt of gratitude, let him escape.

The puzzle recreates that moment on a 4×5 board:

| Block | Size | Who |
|---|---|---|
| 曹操 | 2×2 | Cao Cao — the block you must free |
| 关羽 | 2×1 | Guan Yu, blocking the way |
| 张飞 · 赵云 · 马超 · 黄忠 | 1×2 | The Five Tiger Generals of Shu |
| 兵 | 1×1 | Soldiers |

**Goal:** slide blocks (none may be lifted or overlapped) until Cao Cao reaches the 2-cell opening at the bottom center of the board.

## History

- The puzzle is known in China as **华容道** (*Huarong Dao*), a name given by Professor **Jiang Changying** in his 1949 book *Science Entertainment* (《科学娱乐》).
- A closely related puzzle was patented in England by **J. H. Fleming in 1932**.
- The famous **81-move minimum** for the classic layout was worked out by **Thomas B. Lemann** and published in *Scientific American* (March 1964).
- The same puzzle family appears worldwide: **Klotski** (Poland/West), **箱入り娘** *Hakoiri-musume* (Japan), **L'âne rouge** (France), **Khun Chang Khun Phaen** (Thailand).
- This implementation follows the description at [chinesepuzzles.org](https://chinesepuzzles.org/huarong-pass-sliding-block-puzzle/).

## How to Play

**Controls**
- **Drag** a block in any direction — it slides as far as the empty cells allow. A small soldier (兵) may also turn a corner within a single drag.
- **Or select** a block and use the **arrow keys**, or **click an empty cell** next to it.
- Buttons: **Reset**, **Undo**, **Redo**, **Hint** (plays one optimal move), **Auto-solve** (animates the full optimal solution), sound on/off.

**Move counting** (the classic metric, matching the published 81-move solution)  
One move = sliding one block **any distance in a straight line**; a 1×1 soldier may additionally make **one right-angle turn** within the same move.

**Watch out** — from a solvable start you can still trap yourself! If the built-in solver reports *"no solution from this position"*, undo or reset.

## The 17 Classic Layouts

Named starting configurations from the Chinese puzzle tradition (optimal move counts computed and verified by the built-in solver):

| # | Layout | English name | Optimal |
|---|---|---|---|
| 1 | 横刀立马 | Blocked by Broad Sword and Standing Horses *(the classic)* | **81** |
| 2 | 插翅难飞 | Can't Fly Out, Even with Wings | 62 |
| 3 | 层层设防 | Layered Blockage | 102 |
| 4 | 守口如瓶 | Mouth Sealed Like a Bottle | 81 |
| 5 | 云遮雾障 | Clouds and Fog Block the Way | 81 |
| 6 | 水泄不通 | Not Even Water Can Escape | 79 |
| 7 | 兵分三路 | Troops Split Three Ways | 72 |
| 8 | 四路进兵 | Advance on Four Roads | 77 |
| 9 | 井底之蛙 | Frog in the Well | 68 |
| 10 | 瓮中之鳖 | Turtle in a Jar | 103 |
| 11 | 三军联防 | Three Armies in League | 65 |
| 12 | 屯兵东路 | Troops Garrisoned on the East | 71 |
| 13 | 堵塞要道 | The Pass Is Choked | 40 |
| 14 | 捷足先登 | Swift Feet Arrive First | 32 |
| 15 | 兵临城下 | Soldiers at the City Gate | 54 |
| 16 | 前呼后拥 | Escorted Front and Back | 22 |
| 17 | 峰回路转 | Winding Mountain Road *(hardest known)* | **138** |

The classic layout, for reference:

```
┌────────────────┐
│张飞│    曹操    │赵云│   ← 1×2 generals flank the 2×2 Cao Cao
│    │           │    │
│马超│   关羽    │黄忠│   ← Guan Yu lies directly below him
│    │兵   兵    │    │
│兵  │    ⬇     │ 兵 │   ← the pass at bottom center
└────┘  华容道   └────┘
```

## Built-in Solver

The game includes a breadth-first solver with canonical state deduplication. It reproduces **all published optimal move counts exactly** (81, 62, 102 … 138) and powers the *Optimal* counter, *Hint*, and *Auto-solve*. A regression harness (`test-solver.mjs`) verifies these values against the literature.

## Run It

- **Locally:** just open `index.html` in a browser — it works fully offline.
- **On GitHub Pages:** Settings → Pages → *Deploy from a branch* → `main` / root → the game is live at `https://<you>.github.io/<repo>/`.

## Credits & Data Sources

- Puzzle description, story, and history: [chinesepuzzles.org — Huarong Pass Sliding Block Puzzle](https://chinesepuzzles.org/huarong-pass-sliding-block-puzzle/) (Classical Chinese Puzzle Project).
- The 17 named starting layouts follow the classic collection catalogued at fayaa.com, as compiled in [Simon Hung's Klotski project](https://github.com/SimonHung/Klotski). Optimal counts cross-checked against that literature.
- Game code, solver, and design: original work for this repository.

## License

MIT — do whatever you like with it, attribution appreciated.
