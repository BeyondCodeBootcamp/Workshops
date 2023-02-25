[comment]: # "THEME = white"
[comment]: # "CODE_THEME = github"
[comment]: # "controls: false"
[comment]: # "keyboard: true"
[comment]: # "markdown: { smartypants: true }"
[comment]: # "hash: false"
[comment]: # "respondToHashChanges: false"

Warning:

Live Editing

Mac-centered

Part 1 & 1.5 of 3

---

## Scripting

## &

## Interactive Shell

---

## Interactive Shell

# vs

## Scripting

---

**Fish**

(Interactive Shell)

---

**Posix Shell**

(Scripting)

---

The _NOT_-Bash Parts

(Learn to *Un*learn)

---

### Focus

-   Web Development (& Dev Ops)
    <!-- small>(Dev Opts, _NOT_ Sys Admin)</small -->
-   Know where to start (and stop)
    <!-- small>(and when to stop )</small -->
-   Interpret Feedback
-   Write Clean Scripts (modules, etc)
    <!-- small>(functions, modules, etc)</small -->

---

### Part 1, 2, & 3

---

# Interactive Shell

---

-   Small Brain Paradox
-   First Encounter
-   Not Errors
-   The Tools Make The Man
-   Understanding Makes The Man
-   vi... also makes the man
-   Useful commands

---

## -1. Small Brain

---

1. <https://github.com/new>
2. `shell-cheatsheet`
3. Desc, README, n/a, MPL

<small><a href="https://github.com/BeyondCodeBootcamp/shell-cheatsheet">github.com/BeyondCodeBootcamp/shell-cheatsheet</a></small>

---

````md
# Goal: Install dev tools

A short summary of what we'll do / did.

1. I did this:
    ```sh
    # install xcode command line tools
    xselect --install
    ```
2. I did that
    ```sh
    # install xcode command line tools
    xselect --install
    ```
````

<small><a href="https://github.com/BeyondCodeBootcamp/shell-cheatsheet">github.com/BeyondCodeBootcamp/shell-cheatsheet</a></small>

---

## 0. First Encounter

(how to recover)

---

1. Open the Terminal _thing_
2. Bang on Keyboard
3. TREL the REPL
4. Recover

---

Open Terminal

Bang on Keyboard

---

1. <kbd>Ctrl</kbd> + <kbd>C</kbd> \
   Cancel

---

2. `reset` \
   fix jank

---

3. <kbd>Cmd</kbd> + <kbd>K</kbd> \
   **or**  <kbd>Ctrl</kbd> + <kbd>L</kbd>: \
   KLear the KonsoLe

---

4. <kbd>Ctrl</kbd> + <kbd>D</kbd> \
   **D**one (en**D**)

---

5. Close and Re-Open Terminal

---

Repeat

<small><kbd>Ctrl</kbd> + <kbd>C</kbd> • `reset` • <kbd>Cmd</kbd> + <kbd>K</kbd>/<kbd>L</kbd> • <kbd>Ctrl</kbd> + <kbd>D</kbd> • Re-Open</small>

---

<small><kbd>Ctrl</kbd> + <kbd>C</kbd> • `reset` • <kbd>Cmd</kbd> + <kbd>K</kbd>/<kbd>L</kbd> • <kbd>Ctrl</kbd> + <kbd>D</kbd> • Re-Open</small>

```text
Hello World!

# whatever you want

It's my birthday
```

<small>TREL: Try, Read, Evaluate, Loop</small>

---

<small><kbd>Ctrl</kbd> + <kbd>C</kbd> • `reset` • <kbd>Cmd</kbd> + <kbd>K</kbd>/<kbd>L</kbd> • <kbd>Ctrl</kbd> + <kbd>D</kbd> • Re-Open</small>

```text
echoHelloWorld!

echo Hello World!

echo    Hello    World!

echo    ' Hello    World! '

sudo echo Hello World!

type echo Hello World!
```

<small>(this _should_ all work)</small>

---

<small><kbd>Ctrl</kbd> + <kbd>C</kbd> • `reset` • <kbd>Cmd</kbd> + <kbd>K</kbd>/<kbd>L</kbd> • <kbd>Ctrl</kbd> + <kbd>D</kbd> • Re-Open</small>

```text
time sudo echo Hello World!

sudo time echo Hello World!

echo sudo time Hello World!

history

sudo history
```

<small>(this _should_ all work too)</small>

---

Anything Noteworthy?

---

## 1. Tools Make the Man

---

![macOS](https://user-images.githubusercontent.com/122831/221330438-7bfc8ba2-f4f6-4201-a3c9-20ad36e4969d.png)

https://developer.apple.com/design/resources/

---

<img width="827" alt="Screenshot 2023-02-18 at 7 34 50 PM" src="https://user-images.githubusercontent.com/122831/221330266-02a2fbc9-9211-4fad-9897-e95a716b1f49.png">

---

<img width="827" alt="Screenshot 2023-02-21 at 11 52 09 PM" src="https://user-images.githubusercontent.com/122831/221330347-d8193ae7-2a55-4f75-8dc0-4ac4c0933c9c.png">

---

### OS-Level Dev Tools

---

```sh
# Mac
xcode-select --install
```

```sh
# Linux
sudo apt install -y git vim curl
```

---

### Webi, iTerm, & Rosetta

---

Webi

<https://webinstall.dev/webi>

---

iTerm

<https://webinstall.dev/iterm>

---

Rosetta

<img width="539" alt="Screenshot 2023-02-24 at 7 15 05 PM" src="https://user-images.githubusercontent.com/122831/221330986-f4f4e0fa-dde8-48cd-863e-4b97cce0333c.png">

---

Resetta

<img width="512" alt="Screenshot 2023-02-24 at 7 24 18 PM" src="https://user-images.githubusercontent.com/122831/221331381-b858b305-b447-4242-88ec-3b09724e6a4a.png">

---

### Fish

```sh
command -v fish
```

```sh
webi fish
```

```sh
command -v fish
```

```sh
fish
```

---

<img width="1030" alt="Screenshot 2023-02-24 at 7 28 15 PM" src="https://user-images.githubusercontent.com/122831/221331576-c01a2805-0800-43d9-a6ee-230365e25856.png">

---

### Mo' Dev Tools, Mo' Betta'

```sh
command -v jq
```

```sh
webi aliasman bat curlie \
  fd fzf jq keypairs lsd \
  rg sd serviceman
```

```sh
command -v jq
```

```sh
aliasman cat 'bat --style=plain --pager=none'
aliasman ll 'ls -lAhF'
```

```sh
type cat
```

---

### Rewriting History

```text
fish
exit
command
type
echo
ls
curl
sudo
date
mkdir
time
pushd
popd
git
pwd
history
vi
```

---

What to do?

---

## 2. Useful Commands

---

```sh
git
pushd
popd
cat
curl
jq
```

---

## 3. Understanding Makes the Man

---

```sh
ll

git clone https://github.com/your-username/shell-cheatsheet
ll

pushd ./shell-cheatsheet/
ll

popd
ll

pushd ./shell-cheatsheet/
ll
```

---

https://api.github.com/search/issues?q=type:pr+state:closed+author:coolaj86&per_page=100&page=1

---

Metasyntastic Variables

https://datatracker.ietf.org/doc/html/rfc3092

```text
foobar     quux
foo        corge
bar        grault
baz        garply
qux        waldo
           fred
           plugh
my         xyzzy
your       thud
```

https://en.wikipedia.org/wiki/Metasyntactic_variable

---

## 3. vi... also Makes the Man

(pronounced "vim)

---

```sh

```

---

