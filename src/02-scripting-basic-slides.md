[comment]: # "THEME = white"
[comment]: # "CODE_THEME = github"
[comment]: # "controls: false"
[comment]: # "keyboard: true"
[comment]: # "markdown: { smartypants: true }"
[comment]: # "hash: false"
[comment]: # "respondToHashChanges: false"

Warning:

Live Editing

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

Prep work for upcoming exercises.

---

### 0.1 Webi

Make sure [`webi`](https://webinstall.dev/webi) is installed.

```sh
curl -sS https://webi.sh/ | sh
```

---

### 0.2 Friendly, Interactive Shell

1. Get back into [`fish`](https://webinstall.dev/fish)
    ```sh
    fish
    ```
2. _If_ that fails
    ```sh
    webi fish
    ```
3. TREL. And try again.

---

### 0.3 Vim Essentials

1. Install [`node`](https://webinstall.dev/node) for [`prettier`](https://webinstall.dev/prettier) (code formatter)

    ```sh
    webi node
    node --version

    pathman add ~/.local/opt/node/bin
    node --version

    webi prettier
    ```

2. Install [`vim-essentials`](https://webinstall.dev/vim-essentials) (formatters & linters)
    ```sh
    webi shfmt shellcheck
    webi vim-essentials
    ```

---

### 0.4 Command Line Utilities

[`aliasman`](https://webinstall.dev/aliasman), [`bat`](https://webinstall.dev/bat), [`curlie`](https://webinstall.dev/curlie), [`jq`](https://webinstall.dev/jq)

```sh
webi aliasman bat curlie jq
```

```md
| `aliasman` | create aliases that work cross shells |
| `bat` | `cat` (view) files with colors & paging |
| `curlie` | wrap `curl` with syntax highlighting |
| `jq` | query JSON files and APIs for specific data |
```

---

### 0.4 Temp Directory

Go to a place we can make junk files.

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

## Interactive Shell

(Continued)

---

### Big Goal

Automate, Test and Debug tasks in Terminal

0. Eratta
1. Auto-complete
2. Text Navigation
3. Variables
4. Pipes
5. & Redirection

---

## 0. Eratta

<kbd>Ctrl ???</kbd> + <kbd>s</kbd>

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

<kbd>Ctrl ???</kbd> + <kbd>s</kbd>

<kbd>Ctrl ???</kbd> + <kbd>q</kbd>

---

## 1. Autocomplete Goals

Avoid typos by avoiding typing.

> use the tools, Luke

---

### 1.1 Just TREL

??????

??????

???? <kbd>tab</kbd> ????

Try browsing your history \
(or just typing letters) \
and test the autocomplete.

---

11 out of 10 doctors agree:

> Typing is the leading cause of typos

---

### 2. Navigation Goals

Learn keyboard navigation.

-   emacs-style (line)
-   vim-style (text)

---

### 2.1 Start & End (of Line)

|                                  |                                       |
| -------------------------------- | ------------------------------------- |
| <kbd>Ctrl ???</kbd> + <kbd>a</kbd> | for start (of alphabet), leftmost key |
| <kbd>Ctrl ???</kbd> + <kbd>e</kbd> | for 'end'                             |
|                                  |                                       |

<small>(fyi: these come from emacs, but are nearly-universally supported)</small>

---

### 2.1.1 Exercise

```sh
# type out this line      (alias 'setalias' as 'aliasman')
alias setalias='aliasman'

# but instead of typing this out:
#   1. hit Up to see the previous line
#   2. use Ctrl ??? + a to move to the start of the line
#   3. add 'set' in front of 'alias'
#   4. use Ctrl ??? + e to get back to the end of the line
#   5. hit Enter ??? to run it
setalias setalias='aliasman'
```

<small>(note<span>:</span> the output will tell you to run `alias`, but you've already done that)</small>

---

Repeat for muscle memory!

```sh
# make our interactive `cat` a colorful `bat`
alias cat='bat --style=plain --pager=none'
setalias cat='bat --style=plain --pager=none'
```

Feel the burn!

```sh
# give our interactive `curl` colors
alias curl='curlie'
setalias curl='curlie'
```

---

### 2.2 Text Navigation

????????

????????????????????????????????????????

??????????

---

| <kbd>Shift ???</kbd> | ????  | does the opposite or extreme    |
| ------------------ | --- | ------------------------------- |
| <br>               |     |                                 |
| `gg`, `G`          | ????  | **g**ood **g**ame # 1, opposite |
| `hjkl`             | ????  | awesome goes up to the right    |
| `n`, `N`           | ??????  | **n**ext result, opposite       |

---

### 2.2.1 Exercise

Let's pick a file with a few dozen lines...

```sh
vim ~/.vimrc
```

(updated by [`vim-essentials`](https://webinstall.dev/vim-essentials))

---

???????Reminder

| <kbd>esc</kbd>, `:q!` | quit (immediately) |
| --------------------- | ------------------ |
| `/`                   | search             |
| <kbd>esc</kbd>, `:w`  | write (save)       |

---

1. Go to the top and bottom
    ```sh
    gg  # top of file
    G   # (the opposite)
    ```
2. Go all the way... ????????????????????
    ```sh
    h   # left
    j   # down
    k   # up
    l   # right
    ```
3. Search `/` for "the"
    ```sh
    n   # next result
    N   # (the opposite)
    ```

---

Repeat - build your muscle memory.

Also, try [Vim Adventures](https://vim-adventures.com/).

---

?????? vim-style text navigation works in _many_ places

as we'll see shortly ????

---

## 3. Variables Goals

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

(keep practicing <kbd>Ctrl ???</kbd> + <kbd>a</kbd> and <kbd>Ctrl ???</kbd> + <kbd>e</kbd>)

```sh
echo It\'s   $100   bills y\'all
echo 'It\'s   $100   bills y\'all'

echo "It's   \$100   bills y'all"
echo \"It's   \$100   bills y'all\"
```

---

The file I wanted you to download:

```sh
https://raw.githubusercontent.com/BeyondCodeBootcamp/shell-cheatsheet/main/README.md
```

Too long to fit on a slide!

(time to learn about variables!)

---

Download the url to NOTES.md \
(in the tmp folder)

```sh
# 1. Declare a variable (interactive shell syntax)
#    (note the single quotes)
export my_url='https://raw.githubusercontent.com'

# 2. Add more to that variable
#    (note the double quotes)
export my_url="$my_url/BeyondCodeBootcamp/shell-cheatsheet"
export my_url="$my_url/main/README.md"

# 3. Download using the variable (interactive shell syntax)
#    (note the double quotes, again)
curl -o ./NOTES.md \
    "$my_url"
```

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
vim my-issues.sh
```

---

`vim` Vowels

| <kbd>Shift ???</kbd> | opposite or extreme                  |
| -----------------: | :----------------------------------- |
|                `o` | **o**pen a new line below            |
|            ??? + `O` | _opposite_ of **o**pen below         |
|                `a` | **a**ppend to right edge of cursor   |
|            ??? + `A` | _extreme_ of **a**pend to right edge |
|                `i` | **i**nsert at left edge of cursor    |
|            ??? + `I` | _extreme_ of **i**nsert at left edge |

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
