
# 🧪 Hylab — Build, Test & Deploy ZK Apps on Hyli

> The easiest way to build on Hyli.
> Powered by Risc0 & SP1. Designed for zk developers.

---

## ✨ Why Hylab?

Hylab is a modern developer toolbox and CLI (`hyl`) to build zkApps on [Hyli](https://hyli.org), a privacy-preserving, proof-first blockchain leveraging SP1, Risc0 or Noir. Whether you're prototyping or going to production, Hylab gives you the smoothest path from idea to zk-rollout.

**Main benefits:**

* ✅ Zero-config project scaffolding
* 🚀 Built-in SP1 and Risc0 support (with Noir and more soon)
* 🧪 End-to-end testing made simple
* 🧱 Easy setup local devnet with provers & explorer
* 🔐 Prover network integration (no local proving infra needed)

---

## 🚀 Getting Started

Install the CLI:

```bash
cargo install hyl
```

Then run:

```bash
hyl init my-zkapp
cd my-zkapp
hyl build
hyl net
hyl test
```

That’s it — you’re building on Hyli.

---

## 🧰 CLI Reference

### `hyl init [PROJECT]`

Scaffold a new Hyli zkApp project.

* Ask to choose SP1 or Risc0 as backend
* Clones the default zkApp template
* (soon) Try to validate & setup your local dev environment (Rust, risc0, sp1 toolchains...)
* Noir & Cairo coming soon

```bash
hyl init my-zkapp
```

---

### `hyl build`

Build the project.

```bash
hyl build
```

---

### `hyl clean`

Clean the project build artifacts.

```bash
hyl clean
```

---

### `hyl test`

Run your zkApp’s **end-to-end tests** in a fully orchestrated local Hyli environment.

```bash
hyl test
```

This command automatically spins up a local devnet (`hyl net`), compiles your contracts, deploys them, runs the server and then runs your tests.

#### Key Features

* 🧪 Supports full E2E workflows (from proving to verification)
* ⚙️ Fully integrated with `cargo test` or custom test runners

#### What happens under the hood:

1. Starts `hyl net` if not already running
2. Compiles your project (`hyl build`)
3. Runs your application backend `hyl run`
4. Runs tests defined in `tests/` using `cargo test`
5. Shuts down the devnet & backend after completion (unless `--keep-alive` is set)

#### Example:

```bash
hyl test
```

Want to keep the devnet alive after tests?

```bash
hyl test --keep-alive
```

---

### `hyl net`

Launch a local devnet with:

* Node
* Oranj token contract & Auto-Provers
* Wallet app & Auto-Provers
* Indexer
* Explorer
* Pre-funded test accounts

```bash
hyl net
```

Want a fresh state?

```bash
hyl net --reset
```

---

### `hyl run`

Start your backend service locally or on testnet.
The app backend **registers your contract**, **runs a local auto-prover**, and launches core modules like the **contract indexer**. You can customize the backend in the `server/` folder.

```bash
hyl run
```

By default, `hyl run` operates in local dev mode.

#### Options

* `--testnet`: Register and interact with contracts on the public Hyli testnet.
* `--watch`: Automatically rebuild and re-register on file changes (coming soon)

#### What it does (under the hood):

* ✅ Registers your zk contract on-chain
* 🔁 Starts a local auto-prover (generates and posts proofs when needed)
* 📇 Launches a contract indexer to track state transitions
* 🛠️ Wires everything together for a ready-to-use dev backend

#### Testnet mode (soon):

```bash
hyl run --testnet
```

This will:

* Start the backend connected to the testnet
* Ask to upload your contract on the prover network


---

## 📡 Upload to the Prover Network (Soon)

Upload your compiled ELF to the **Hyli Prover Network**, allowing proofs to be generated off-chain by a prover network.

This is especially useful on testnet where you want to avoid setting up local proving infrastructure.

```bash
hyl upload
```

**What it does:**

* Validates the ELF format
* Register the contract on the prover network given the ELFs

**Why use it?**

* ⚡ Avoid local proving (faster dev loop)
* 🌍 Share proof artifacts with teammates or collaborators
* 🧱 Make your app testnet-ready without running provers


---

## 🧠 Under the Hood

Hylab builds on top of:

* **SP1/Risc0 zkVM** for fast, verifiable compute
* **Rust** for native speed and tooling compatibility

Coming soon:

* 🧑‍🎨 Noir Integration (Q4 2025)
* 🌀 Cairo Exploration
* 📦 Custom Prover Uploads via `hyl upload`

---

## 🧪 Try It Out

We’re just getting started. If you're testing Hylab early:

* Open issues or ideas [here](https://github.com/hyli-org/hyli/issues)
* Share feedback with the Hyli team
* Ping us with questions!

---

## 🛤️ Whishlist

* [ ] Noir support
* [ ] Cairo experiments
* [ ] Plugin system for custom commands
* [ ] zkApp deployment templates

---

## ❤️ Built with Love by the Hyli Team

---


