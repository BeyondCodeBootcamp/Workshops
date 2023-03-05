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

Part 1.5 & 2 of 3

---

## Interactive Shell

# vs

## Scripting

---

## Interactive Shell

---

## Scripting

---

**Posix Shell**

(Scripting)

---

The _NOT_-Bash Parts

(Learn to *Un*learn)

---

## Part 1.5 Continued

---

# TREL

---

-   **T**ry
-   **R**ead (what's on the screen)
-   **E**valuate (with your human brain)
-   **L**oop (back to try again)

---

The equal and opposite of the REPL.

<small>(the human loop between your fingers, the screen, and your brain)</small>

---

# REPL

---

-   **R**ead (from the keyboard)
-   **E**valuate (syntax and expressions)
-   **P**rint (the error or result)
-   **L**oop

---

There is no magic.

<small>(the computer does what you say, not what you <em>want</em>)</small>

---

## 0. Pre-req

---

### 0.1 Webi

Make sure `webi` is installed.

```sh
curl -sS https://webi.sh/ | sh
```

---

### 0.2 Interactive Shell

(exercises ahead)

---

Get back into `fish`.

```sh
fish
```

If that fails:

```sh
webi fish
```

TREL. And try again.

---

### 0.3 Temp Directory

(junk and test files ahead)

---

Go to the temp directory.

<small>(and make sure you're there)</small>

```sh
pwd
```

```sh
pushd /tmp/
pwd
```

```sh
popd
pwd
```

```sh
pushd /tmp/
```

---

## 1. Interactive Concepts

---

0. Eratta
1. Auto-complete
2. Text Navigation
3. Variables
4. Pipes
5. & Redirection

---

## 0. Eratta

<kbd>Ctrl ⌃</kbd> + <kbd>s</kbd>

-   This is called "scroll lock".
-   It freezes _some_ shells (`bash`, `sh`), \
    but not all (e.g. `fish`)

<small>(nor any shell spawned from fish)</small>

---

Try in a terminal or console \
where `bash` is the parent shell:

```sh
find /
```

<kbd>Ctrl ⌃</kbd> + <kbd>s</kbd>

<kbd>Ctrl ⌃</kbd> + <kbd>q</kbd>

---

## 1.1 Autocomplete

11 out of 10 doctors agree:

> Typing is the leading cause of typos

---

Try browsing your history \
(or just typing letters) \
and test the autocomplete:

⬆️

➡️

🎩 <kbd>tab</kbd> 🪄

---

### 2. Navigation

**Goal**: Learn keyboard navigation.

(emacs-style and vim-style)

---

### 2.0 Some Tools

```sh
webi aliasman curlie bat jq
```

---

Note<span>: We won't use this "for real" until later.

<small>For now they'll just give us an excuse to explore some navigation.</small>

---

### 2.1 Beginning and End of Line

| Combo                            | Desc                                             |
| -------------------------------- | ------------------------------------------------ |
| <kbd>Ctrl ⌃</kbd> + <kbd>a</kbd> | A, the first letter,<br> goes to first character |
| <kbd>Ctrl ⌃</kbd> + <kbd>e</kbd> | E for 'end'                                      |

<small>(fyi: these come from emacs, but are nearly-universally supported)</small>

---

### 2.2 Exercise

```sh
# type out this line      (alias 'setalias' as 'aliasman')
alias setalias='aliasman'

# but use up and ctrl + a to edit this line
setalias setalias='aliasman'
```

```sh
# get that muscle memory   (make our interactive cat a bat)
alias cat='bat --style=plain --pager=none'
setalias cat='bat --style=plain --pager=none'
```

```sh
# feel the burn!         (give our interactive curl colors)
alias curl='curlie'
setalias curl='curlie'
```

---

### Goal 1.1

Learn to diagnose unexpected results

(quotes, variables, and interpolation)

---

1. What do you think this will output?
    ```sh
    echo It's   $100   bills y'all
    ```
2. Try it.
3. Is anything different what what you thought?

---

1. What's different about this?
    ```sh
    echo "It's   $100   bills y'all"
    ```
2. What will it do differently?
3. Try it.
4. Is anything different what what you thought?

---

What about each of these?

```sh
echo It\'s   $100   bills y\'all
echo 'It\'s   $100   bills y\'all'
echo "It's   \$100   bills y'all"
echo \"It's   \$100   bills y'all\"
```

---

### Goal 1.2

The url I wanted to show is too long to fit on a slide.

---

That's okay. We can

1. Declare a variable (interactive shell syntax)
    ```sh
    export my_url='https://raw.githubusercontent.com'
    ```
2. Add more to that variable
    ```sh
    export my_url="$my_url/BeyondCodeBootcamp/shell-cheatsheet"
    export my_url="$my_url/main/README.md"
    ```
3. Use the variable (interactive shell syntax)
    ```sh
    curl -o ./NOTES.md \
        "$my_url"
    ```

---

```sh
vim ./NOTES.md
```

| <kbd>esc</kbd> | `:q!`  |
| -------------- | ------ |
| `/`            | search |
| <kbd>esc</kbd> | `:wq`  |

---

| <kbd>Shift ⇧</kbd> | does the opposite or extreme |
| ------------------ | ---------------------------- |
| `n`                | **n**ext                     |
| `N`                | _opposite_ of next           |
| `gg`               | **g**ood **g**ame # 1        |
| `G`                | opposite of #1               |
| `hjkl`             | awesome goes up to the right |

---

```sh
/bin/cat ./NOTES.md
cat ./NOTES.md
less ./NOTES.md
bat ./NOTES.md

rm ./NOTES.md
cat ./NOTES.md
```

---

```sh
curl "$my_url"

curl "$my_url" |
    bat

curl "$my_url" |
    less

curl "$my_url" \
    > ./NOTES.md

bat ./NOTES.md
```

---

```sh
curl "$my_url" \
    > ./NOTES.md \
    2> ./log.txt

bat ./log.txt
```

---

```sh
export my_url='https://api.github.com/search/issues'
export my_url="$my_url?q=type:pr+state:closed"
export my_url="$my_url+author:coolaj86"
export my_url="$my_url&per_page=2&page=1"
```

```sh
curl "$my_url"
curl "$my_url" > \
    ./gh-issues.json
```

---

```sh
bat ./gh-issues.json

bat < ./gh-issues.json

bat ./gh-issues.json |
    jq '.'

cat ./gh-issues.json |
    jq '.total_count'

jq '.total_count' < ./gh-issues.json
```

---

```sh
jq '.items' < ./gh-issues.json
jq '.items[]' < ./gh-issues.json
jq '.items[0]' < ./gh-issues.json
jq '.items[].url' < ./gh-issues.json
jq '.items[0].url' < ./gh-issues.json
```

---

| Director     | Description                    |
| :----------- | :----------------------------- | ------------------- |
| `>`          | **replace** file with _stdout_ |
| `<`          | _stdin_ from file              |
| `            | `                              | _stdout_ to _stdin_ |
| `2>`         | _stderr_ to file               |
| upcoming     |                                |
| `>>`         | append _stdout_ to file        |
| `> /dev/tty` | write to **t**erminal          |

---

## vim 1.3

---

```sh
webi node
node --version

pathman add ~/.local/opt/node/bin
node --version

webi prettier shfmt shellcheck
webi vim-essentials
```

```sh
vim my-issues.sh
```

---

`vim` Vowels

| <kbd>Shift ⇧</kbd> | opposite or extreme                  |
| -----------------: | :----------------------------------- |
|                `o` | **o**pen a new line below            |
|            ⇧ + `O` | _opposite_ of **o**pen below         |
|                `a` | **a**ppend to right edge of cursor   |
|            ⇧ + `A` | _extreme_ of **a**pend to right edge |
|                `i` | **i**nsert at left edge of cursor    |
|            ⇧ + `I` | _extreme_ of **i**nsert at left edge |

---

`vim` Deutschlandics

|     (wolks | vagon)                        |
| ---------: | :---------------------------- |
|        `u` | **u**ndo                      |
|        `v` | **v**isually select           |
|        `d` | **d**elete (for Deutschland!) |
| `v` + `du` | ... copy                      |
|        `p` | **p**aste                     |

---

```vim
:message
```

---

## Scripting 1.1

---

-   `PATH`
-   `x` bit
-   `shebang`

---

```sh
mkdir -p ~/bin
touch ~/bin/my-issues.sh
chmod a+x ~/bin/my-issues.sh

pathman add ~/bin/

my-issues.sh
```

---

```sh
export my_user=coolaj86
export my_limit=100
export my_page=2

my-issues.sh "$my_user" "$my_limit" "$my_page"

my-issues.sh "$my_user"

my-issues.sh "$my_user" "$my_limit"

```

---

```sh
export my_user=coolaj86
export my_limit=100
export my_page=2

my-issues.sh "$my_user" "$my_limit" "$my_page"

my-issues.sh "$my_user" "$my_limit" # default page 1

my-issues.sh "$my_user" # default 10 items

```

---

```sh
echo #!/bin/sh >> ~/bin/my-issues.sh

echo '#!/bin/sh' >> ~/bin/my-issues.sh
my-issues.sh
```

---

## Scripting 1.2

---

-   _strict_ mode
    -   `set -e`
    -   `set -u`
-   _arguments_
    -   `${0:-} ... ${999:-}`
    -   `${@:-}`
    -   `${*:-}`
-   _functions_
    -   `foo() {( ... )}`
-   _test_ & `grep`

---

```sh
#!/bin/sh
set -e
set -u

# 1. handle arguments & set vars
my_name="${1:-}"

# 2. define functions
main() { (

  echo "${my_name}"

); }

# 3. do stuff
main "foobar"
```

---

```sh
  ...

  echo "${my_name}"

  false

  echo "I'm bad"

  ...
```

---

```sh
  ...


  if false; then
    echo "I'm good"
  else
    echo "I'm bad"
  fi


  ...
```

---

```sh
  ...


  my_num=$(( my_num + 1 ))


  ...
```

---

## Scripting 1.3

---

-   _subshells_
    -   `"$( ... )"`
-   _math shells_
    -   `$(( ... ))`
-   _text expansion_
    -   `{ ... }`

---

```sh
curl https://example.com/
```

```sh
curl 'https://api.github.com/search/issues?q=type:pr+state:closed+author:coolaj86&per_page=100&page=1'
```

---

-   function
-   return
-   test
-   exit

---
