# findR

## Introduction

findR is a command-line tool designed to search for specific patterns within R, R Markdown, and Stata .do files. It provides functionalities to search for patterns, print matching filenames, and optionally open the matching files in RStudio.

## Installation

- Change l38 to your chosen default directory.
- Paste the enclosed functions into your .zshrc file.
- Note: .zshrc is usually found in `~/Users/Name/`. To display hidden system files press `cmd` + `shift` + `.`


## Usage

### Requirements

- **Operating System**: macOS
- **Terminal**: zsh
- **Software**: RStudio

### Syntax

```bash
findR [OPTIONS] pattern
```

### Options

- **-d, --dir**: Specify the directory to search in. By default, it searches in `/Users/`.
- **-l, --limit**: Limit the number of search results to display. By default, it shows up to 999999 results.
- **-o, --open**: Open the matching files in RStudio.
- **-f, --filenames**: Print only the filenames containing the matching patterns.

### Arguments

- **pattern**: The pattern to search for within the R, R Markdown, and Stata .do files.

## Functions

### 1. `findR`

The main function responsible for searching for patterns within files.

#### Syntax

```bash
findR [OPTIONS] pattern
```

#### Options

- **-d, --dir**: Specify the directory to search in.
- **-l, --limit**: Limit the number of search results to display.
- **-o, --open**: Open the matching files in RStudio.
- **-f, --filenames**: Print only the filenames containing the matching patterns.

### 2. `openR`

Opens a specific file in RStudio.

#### Syntax

```bash
openR index
```

#### Arguments

- **index**: The index of the file to open. This corresponds to the index displayed when search results are shown.

## Examples

1. Search for the pattern "data.frame" in the default directory:
  
  ```bash
findR data.frame
```

2. Search for the pattern "plot" in a specific directory and open matching files in RStudio:
  
  ```bash
findR -d ~/Projects -o plot
```

3. Print filenames for files containing the pattern "library" without searching recursively:
  
  ```bash
findR -d ~/Documents -f library
```

4. Print filenames for files containing the pattern "dplyr" OR "ggplot2":

```bash
findR -f "(dplyr|ggplot2)" 
```

5. Print filenames for files containing the pattern "dplyr" AND "ggplot2":

```bash
findR -f "dplyr.*ggplot2|ggplot2.*dplyr"
```

6. Open the fifth line returned by the terminal:

```bash
openR 5
```

## Notes

- The search uses extended grep (`grep -E`) and is case-insensitive by default.
- The script searches in .R, .Rmd, and .do files.
- You must have RStudio installed for the `-o` option to work.

## Version

1.0.0
