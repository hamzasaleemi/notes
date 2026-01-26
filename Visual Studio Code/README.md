# Visual Studio Code Notes

## Go to File
Search a file and then open it. Usage:
- Press `ctrl + P`
- Search File
- Press `enter`

## Multiple Cursors
- Hold `alt` and click where you want cursor.

## Select All Occurances
- While something is selected press `ctrl + shift + L` to 

## Select Next Occurance
- Press `ctrl + D`

## Move Current Line Up or Down
- Hold `alt` and press `up` or `down`

## Copy Current Line Down
- Hold `alt + shift` and press `down`

## Find in Files
Search something in project files.
- Press `ctrl + shift + F`
- Enter search text and we will get results.

## Extensions
- Press `ctrl + shift + X` to open extensions menu
- `@sort:installs` Sorts extensions by most installs
- `@installed` Show only installed extensions

### Advance New File Extension
- Press `ctrl + alt + N` to create a new file

### File Utils
This extension helps in creating, renaming, duplicating, deleting files.

### Git Lens
Enhance your workflows with powerful Git functionality like in-editor blame annotations, hovers, CodeLens, and more all fully customizable within VS Code.

### Laravel Artisan
Run all your artisan commands quicky through command palette.

### Better PHPUnit
Better PHPUnit is the most popular, cleanest, and fastest PHPUnit runner for VS Code.

### PHP CS Fixer
This extension simply provides PHP CS Fixer command.
`https://github.com/junstyle/vscode-php-cs-fixer`

### XDebug
- Install XDebug in your php extensions
- Install XDebug extension in VS Code.
- Add Configurations in your workspace.
- Start Debug of VS Code
- Start your project server

### Import Cost
This extension will display inline in the editor the size of the imported package. The extension utilizes webpack in order to detect the imported size.

### ESLint
Integrates ESLint into VS Code.

## Command Palette
- Press `ctrl + shift + P`

## Settings
- Press `ctrl + ,`

## Keyboard Shortcuts
- Press `ctrl + K` then `ctrl + S` to open keyboard shortcuts

## Context Menu
- Press `shift + F10` to open context menu

## SideBar
- Press `ctrl + b`

## Symbol
Scroll screen to and highlights code in file or workspace.
- Press `ctrl + shift + O` to search symbol in file.
- Press `ctrl + T` to search symbol in workspace.

## Snippets
Create your own snippets to speed up coding. Enable tab completion in User Settings.

### Tabstops
With tabstops, you can make the editor cursor move inside a snippet. Use `$1`, `$2`, `$0`

### Placeholders
Placeholders are tabstops with values, like `${1:foo}`

### Variables
- `TM_SELECTED_TEXT` The currently selected text or the empty string
- `TM_CURRENT_LINE` The contents of the current line
- `TM_CURRENT_WORD` The contents of the word under cursor or the empty string
- `TM_LINE_INDEX` The zero-index based line number
- `TM_LINE_NUMBER` The one-index based line number
- `TM_FILENAME` The filename of the current document
- `TM_FILENAME_BASE` The filename of the current document without its extensions
- `TM_DIRECTORY` The directory of the current document
- `TM_FILEPATH` The full file path of the current document
- `RELATIVE_FILEPATH` The relative (to the opened workspace or folder) file path of the current document
- `CLIPBOARD` The contents of your clipboard
- `WORKSPACE_NAME` The name of the opened workspace or folder
- `WORKSPACE_FOLDER` The path of the opened workspace or folder
- `CURSOR_INDEX` The zero-index based cursor number
- `CURSOR_NUMBER` The one-index based cursor number
- `CURRENT_YEAR` The current year
- `CURRENT_YEAR_SHORT` The current year's last two digits
- `CURRENT_MONTH` The month as two digits (example '02')
- `CURRENT_MONTH_NAME` The full name of the month (example 'July')
- `CURRENT_MONTH_NAME_SHORT` The short name of the month (example 'Jul')
- `CURRENT_DATE` The day of the month as two digits (example '08')
- `CURRENT_DAY_NAME` The name of day (example 'Monday')
- `CURRENT_DAY_NAME_SHORT` The short name of the day (example 'Mon')
- `CURRENT_HOUR` The current hour in 24-hour clock format
- `CURRENT_MINUTE` The current minute as two digits
- `CURRENT_SECOND` The current second as two digits
- `CURRENT_SECONDS_UNIX` The number of seconds since the Unix epoch
- `CURRENT_TIMEZONE_OFFSET` The current UTC time zone offset as `+HH:MM` or `-HH:MM` (example `-07:00`).
- `BLOCK_COMMENT_START` Example output: in PHP `/*` or in HTML `<!--`
- `BLOCK_COMMENT_END` Example output: in PHP `*/` or in HTML `-->`
- `LINE_COMMENT` Example output: in PHP //
- `RANDOM` 6 random Base-10 digits
- `RANDOM_HEX` 6 random Base-16 digits
- `UUID` A Version 4 UUID

## Terminal
- To open terminal Press `ctrl` + `

## Git
- To open source control Press `ctrl + shift + G`