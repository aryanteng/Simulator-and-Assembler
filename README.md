# Assembler and simulator for a custom ISA

An assembler and an instruction-level simulator for the toy 16-bit ISA from IIIT-Delhi's Computer Organisation course (Monsoon 2021), in Python 3. The simulator also uses matplotlib to plot its execution trace.

- **Assembler** (`Simple-Assembler/assembler.py`): reads assembly from stdin and writes 16-bit machine code to stdout. It resolves labels and variables, encodes 19 instructions across the ISA's register, immediate, memory and jump formats, and reports errors with line numbers instead of emitting bad code. The errors it catches include syntax and register-name typos, illegal immediates, undefined variables, misuse of FLAGS, late `var` declarations and a missing `hlt`.
- **Simulator** (`SimpleSimulator/simulator.py`): executes the binary on a 256-word memory with registers R0–R6 and FLAGS. After every instruction it prints the program counter and register state, and at `hlt` it dumps all 256 words of memory and plots the trace.

Instructions: `add sub mov ld st mul div rs ls xor or and not cmp jmp jlt jgt je hlt`.

## Run

```bash
python3 Simple-Assembler/assembler.py < program.asm > program.bin
python3 SimpleSimulator/simulator.py < program.bin
```

## Tests

`automatedTesting/` is the grading harness the course staff provided, with simple, hard and error-case programs:

```bash
cd automatedTesting && ./run --verbose   # --no-asm or --no-sim to test one half
```

Built as a team course project; the harness and test programs are the course staff's.
