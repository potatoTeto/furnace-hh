# Game Boy

the Game Boy is one of the most successful portable game systems ever made.

it has stereo sound, two pulse channels, a wave channel and a noise channel.

## effects

- `10xx`: **change wave.**
- `11xx`: **set noise length.**
  - `0`: long
  - `1`: short
- `12xx`: **set duty cycle.**
  - `0`: 12.5%
  - `1`: 25%
  - `2`: 50%
  - `3`: 75%
- `13xy`: **setup sweep.** pulse channels only.
  - `x` is the time.
  - `y` is the shift.
  - set to `0` to disable it.
- `14xx`: **set sweep direction.** `0` is up and `1` is down.

# supported engines

## MMLGB

the MMLGB export feature produces a single .mml file, to be provided to the MMLGB compiler utility. the export feature can be accessed via [file] -> [export MML-GB...] -> [export]

### supported features

  | feature               | support             |
  | --------------------- | ------------------- |
  | instrument macros     | partial<sup>[1](#notes)</sup> |
  | global tuning         | none<sup>[2](#notes)</sup> |
  | hardware envelopes    | partial<sup>[3](#notes)</sup> |
  | software envelopes    | none                |
  | wavetables            | full                |

### supported chip effects

  | effect | description                 | support |
  | ------ | --------------------------- | ------- |
  | `10xx` | change wave                 | full    |
  | `11xx` | set noise length            | full    |
  | `12xx` | set duty cycle              | full    |
  | `13xx` | setup sweep                 | none    |
  | `14xx` | set sweep direction         | none    |

### supported general effects

  | effect | description                   | support |
  | ------ | ----------------------------- | ------- |
  | `00xy` | arpeggio                      | none    |
  | `01xx` | slide up                      | none    |
  | `02xx` | slide down                    | none    |
  | `03xx` | note portamento               | none    |
  | `04xy` | vibrato                       | none    |
  | `07xy` | tremolo                       | none    |
  | `08xy` | set panning                   | full    |
  | `80xx` | set panning (linear)          | full    |
  | `81xx` | set volume of left channel    | none    |
  | `82xx` | set volume of right channel   | none    |
  | `09xx` | set speed 1                   | full    |
  | `0Axy` | volume slide                  | none    |
  | `0Bxx` | jump to pattern               | full    |
  | `0Cxx` | retrigger note                | full    |
  | `0Dxx` | jump to next pattern          | full    |
  | `0Fxx` | set speed 2                   | full    |
  | `9xxx` | set sample position           | n/a     |
  | `Cxxx` | change song Hz                | full    |
  | `E0xx` | set arpeggio tick             | none    |
  | `E1xy` | note slide up                 | none    |
  | `E2xy` | note slide down               | none    |
  | `E3xx` | set vibrato direction         | none    |
  | `E4xx` | set vibrato range             | none    |
  | `E5xx` | set pitch                     | none    |
  | `EAxx` | toggle legato                 | none    |
  | `EBxx` | set sample bank               | n/a     |
  | `ECxx` | note off after `xx` ticks     | full    |
  | `EDxx` | delay note by `xx` ticks      | full    |
  | `EExx` | send external command         | none    |
  | `EFxx` | add or subtract global pitch  | none    |
  | `F0xx` | change song Hz by BPM value   | full    |
  | `F1xx` | single tick slide up          | none    |
  | `F2xx` | single tick slide down        | none    |
  | `F3xx` | fine volume slide up          | none    |
  | `F4xx` | fine volume slide down        | none    |
  | `F8xx` | single tick volume slide up   | none    |
  | `F9xx` | single tick volume slide down | none    |
  | `FAxy` | fast volume slide             | none    |
  | `FFxx` | end of song/stop playback     | full    |

### quirks and limitations
  - noise frequency mapping is not 1:1, due to MMLGB's noise table missing some key frequencies.
    - this can be fixed by unchecking the "Legacy" option upon export, if using [the modified engine](https://github.com/jimmy-dsi/mmlgb).

### notes
  1. only the first tick of duty and wave macros are supported. no other macro types are yet supported.
  2. locked at A-4 = 440Hz.
  3. volume and length only (no sound length).

## info

this chip uses the [Game Boy](../4-instrument/game-boy.md) instrument editor.

## links

- [Gameboy sound hardware](https://gbdev.gg8.se/wiki/articles/Gameboy_sound_hardware) - detailed technical information

- [GameBoy Sound Table](http://www.devrs.com/gb/files/sndtab.html) - note frequency table
