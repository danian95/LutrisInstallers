Native ScummVM Lutris Installers
================================

Intro (feel free to skip)
-------------------------

I'm excited about my son getting old enough to play some of the classic
PC games I grew up with. Fortunately, I bought the Humongous
Entertainment Complete Pack on Humble when it was on sale a long time ago, so I
have digital copies of the old games I did own (Putt-Putt and Fatty Bear,
specifically) and a lot that I did not (Pajama Sam, Freddi Fish, Spy Fox).

The problem is that I don't really want all these games installed on Steam for
the following reasons:

* It fills up my library with games that I'm never going to seek out on my own.
* Each game adds its own bundled (and outdated) ScummVM version.
* I don't want to install Steam (yet) on whatever computer he's going to start using
  first.

Installers
----------

The general layout consists of some identifying information.

```yaml
game_slug: freddi-fish-and-the-case-of-the-missing-kelp-seeds
name: 'Freddi Fish and The Case of the Missing Kelp Seeds'
steamid: 283940
slug: freddi-fish-and-the-case-of-the-missing-kelp-seeds-steam-scummvm-native
version: Steam with Native ScummVM
year: 1994
runner: scummvm
  ```
And the script in which we identify only the files we need to run each game
locally and copy them into `$GAMEDIR`.

* The required files where the path is determined automatically, following the
  proper Steam paths:

  ```yaml
  files:
    - HE0: $STEAM:283940:FREDDI.HE0
    - HE1: $STEAM:283940:FREDDI.HE1
    - HE2: $STEAM:283940:FREDDI.HE2
    - HE3: $STEAM:283940:FREDDI.HE3
    - HE4: $STEAM:283940:FREDDI.HE4
  ```

  It seems like the installer just asks for files as well, so if you use an
  original CD, you may be able to select these specific files.

* Some game information which tells Lutris how to find the game, the ScummVM
  identifier, and the working directory (where we'll install the game).

  ```yaml
  game:
    appid: 283940
    game_id: scumm:freddi
    path: $GAMEDIR
  ```

* The installation process, which is just copying each of the named files above
  to the `$GAMEDIR` (installation directory).

  ```yaml
  installer:
    - merge:
        dst: $GAMEDIR/
        src: $HE0
    - merge:
        dst: $GAMEDIR/
        src: $HE1
    - merge:
        dst: $GAMEDIR/
        src: $HE2
    - merge:
        dst: $GAMEDIR/
        src: $HE3
    - merge:
        dst: $GAMEDIR/
        src: $HE4
  ```
