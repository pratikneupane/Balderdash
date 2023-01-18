# Balderdash [WIP]

Balderdash is a profanity checker tool for your codebase. It was created to that you
won't have to worry about mistakenly commiting curse words or some not-so-appropriate
words to your main branch.

It's a simple shell script and can run on almost any Unix system. It was created in
shell due to how simple it was to write it. I have no plans of moving it to other
languages and adding more graphic features.

## Installation

You'll need to have [ag](https://github.com/ggreer/the_silver_searcher) installed
in your system. `ag` is very fast code searcher.

The following script adds balderdash script to your `/bin`.

```bash
curl -L https://raw.githubusercontent.com/CaffeineDuck/Balderdash/main/install.sh | bash
```

You'll need to run init after installing the script.

```bash
balderdash init
```

## Using pre-commit hook

Add to your hooks.

```yaml
repos:
  - repo: https://github.com/caffeineDuck/balderdash
    rev: $LATEST_VERSION
    hooks:
      - id: balderdash
```

## CLI Usage Examples

- Checking the current directory for profanity

```bash
balderdash check
```

- Checking specific dir for profanity

```bash
balderdash check -d dir/
```

- Checking specific file for profanity

```bash
balderdash check -f app.py
```

- Checking from your custom parsed wordlist

```
bash check -f app.py -w parsed_wordlist.txt
```

`Note:` _Your wordlist must follow Extended Regex format_

## CLI Reference

```bash
Balderdash is a tool to find profanity in files

Usage: balderdash [command] [options]

Commands:
  init|i: Initialize the config file
  help|h: Display this help message
  check|c <-f|-c|-w|-s|-d>: Check a file/dir for profanity
  download|dw <-c>: Download the profanity list according to language selection

Options:
  -f [FILE]: Specify a file to check
  -c [FILE]: Specify a config file
  -d [DIR]: Specify a directory to check
  -w [FILE]: Specify a file containing profanity words list
  -s: Strict mode. Exit with error code 1 if profanity is found
```
