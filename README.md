# History

History is a zsh script which internally uses python to handle data. 

With this script, you can easily find any command you've executed and call it again.

## How to use

Use command `h` followed by key word you want to search:

```bash
h grep
```

Then you will get all commands contains 'grep', each line begins with a number.

To call a specific line, you just need to type the number(for eaxmple `1`):

```bash
1
```

## How to install

Firstly, you need to clone the repository:

```bash
git clone https://github.com/bestswifter/history.git ~/.history
```

Then, you need to add the script below to your .zshrc to make sure it's sourced everytime a new zsh process is started:

```bash
function h() {
    python ~/.history/history.py $1
    cat ~/.history/.histfile_func | while read -r line; do eval "$line" &>/dev/null;done
}
```

## TO-DO

1. Limit maximum lines of output
2. Use shell command `history` instead of grep a file
3. Support serach directories you've visited