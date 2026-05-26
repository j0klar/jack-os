# jack-os

An implementation of the Jack OS standard/runtime library written in Jack, acting as the operating system for the Hack computer and built as part of the [Nand2Tetris](https://www.nand2tetris.org/) course (Project 12).

Provides a variety of runtime services that compiled Jack programs depend on: memory allocation, integer arithmetic, screen and text I/O, keyboard input, bootstrapping, string and array handling.

For a detailed overview of the entire computing system and compilation process, [click here](https://github.com/j0klar/jack-compiler).


## Usage

```bash
python compiler.py MyApp/       # MyApp/ contains .jack OS files + app files
```

Compile the OS together with a Jack application in the same directory using the [Jack compiler](https://github.com/j0klar/jack-compiler).


## Modules

**Memory:** `peek`, `poke`, `alloc`, `deAlloc` - heap-based dynamic memory management using a linked free list (heap base at RAM address 2048, initial free size of 14334 words).

**Math:** `multiply`, `divide`, `sqrt`, `min`, `max`, `abs` - O(n) algorithms for multiplication, division, and integer square root calculation.

**Screen:** `clearScreen`, `setColor`, `drawPixel`, `drawLine`, `drawRectangle`, `drawCircle` - direct access to the 512×256 pixel memory-mapped screen starting at RAM address 16384, Bresenham-style line drawing.

**Output:** `moveCursor`, `printChar`, `printString`, `printInt`, `println`, `backSpace` - text output on a 23×64 character grid using an embedded 8×11 pixel font (ASCII 32–126).

**Keyboard:** `keyPressed`, `readChar`, `readLine`, `readInt` - press-and-release monitoring of the memory-mapped keyboard at RAM address 24576.

**String:** `new`, `dispose`, `length`, `charAt`, `setCharAt`, `appendChar`, `eraseLastChar`, `intValue`, `setInt` - mutable character arrays with int-to-string and string-to-int conversion.

**Array:** `new`, `dispose` - array initialization and disposal.

**Sys:** `init`, `halt`, `error`, `wait` - boot sequence, error reporting, and timing.


## Dynamic Memory Management

![Memory Management](memory-alloc.png)

*Source: Nisan & Schocken, The Elements of Computing Systems, 2nd ed. MIT Press (2021), Slides 60-61 (modified).*


## Project Structure

```
jack-os/
├── Memory.jack
├── Math.jack
├── Screen.jack
├── Output.jack
├── Keyboard.jack
├── String.jack
├── Array.jack
├── Sys.jack
└── memory-alloc.png
```
