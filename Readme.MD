# Rootstock CLI Pipe Command

A proposal to extend the **Rootstock CLI** with **pipe (`|`) command support**, enabling seamless chaining of commands.

This tool allows developers to **pipe outputs from one command into another**, automating workflows such as:

- Deploying a smart contract and automatically verifying it.
- Sending a transaction and immediately checking its confirmation status.
- Chaining multiple CLI actions into a single, efficient command.

---

## Why This Matters

**Problem:** Current Rootstock CLI requires running commands separately, manually copying outputs like transaction hashes or contract addresses. This slows down workflows and increases error risk.

**Solution:** Introduce a **pipe mechanism** that captures outputs and feeds them directly into subsequent commands.

This enhancement improves **developer experience, efficiency, and automation** for the Rootstock ecosystem.

---

## Features

- **Pipe Command Support** → Use `|` to chain CLI commands.  
- **Automatic Input Handling** → Pass outputs (transaction hash, contract address, etc.) to the next command.  
- **Flexible Output Formats** → Support `--json`, `--raw`, `--pretty` for piping.  
- **Error Handling** → Graceful failure; if one step fails, subsequent steps won’t execute.  
- **Debugging Tools** → Verbose logging with `--debug`.  

---

## Example Usage

```bash
# Deploy contract, pipe deployed address into verify command
rsk-cli deploy MyContract.sol | rsk-cli verify

# Send transaction and pipe hash into status
rsk-cli transfer --to 0x123 --value 1 | rsk-cli tx-status
Technical Outline
Required Features
Pipe command support

Automatic input handling

Error handling & exit codes

Configurable output formatting

Key Functions
pipeExecutor(commandChain: string[]) → Executes chained commands sequentially.

formatOutput(output: any, format: string) → Formats output for piping.

parseInput(input: string) → Detects hashes/addresses.

errorHandler(error: any) → Standard error handling & exit codes.

## Dependencies
Node.js (CLI implementation)

Rootstock CLI base package

## Skills Required
Node.js / TypeScript → CLI development

Rootstock / EVM Knowledge → Understand transactions & contract deployment

Shell / CLI Design → Piping and process management

Testing (Mocha/Jest) → Ensure command chaining works reliably

## Project Structure

rootstock-cli-pipe/
│
├── src/
│   ├── pipeExecutor.ts   # Core executor logic
│   └── utils.ts          # Helpers for parsing/formatting
│
├── tests/
│   └── pipeExecutor.test.ts
│
├── README.md
├── package.json
└── .gitignore

##References
Rootstock Docs

Unix Pipe Concept

Inspiration: hardhat task runner & docker CLI piping

Contribution
Contributions are welcome!

Fork the repo

Create a feature branch

Submit a PR

License
MIT License









