# jsew

.js (or .css or any other you like) files sewing tool. Adds "include" directive
with auto-indent handling making possible binding of all separate files to one.

## Usage

```
Usage: ./jsew [options] <input-file>

Options:
  -o <out-file> --out <out-file>    - save to out-file. Will only try to overwrite
                                      when any component change date is more recent
                                      than the out-file
  -f            --force             - force out-file overwrite, regardless of
                                      component files change date
  -d <path>     --dir <path>        - same as cd <path> ; jsew [...]
  -p <cmd>      --postprocess <cmd> - pipe contents through given command
  -c <file>     --copy <file>       - prepend output with file(s) contents (after
                                      eventual postprocess). Will also be included
                                      in files index
  -b <file>     --before <file>     - same as -c, but before postprocess
  -a <file>     --after <file>      - same as -b, but append instead of prepending
  -i            --index             - index files and exit
  -v            --verbose           - verbose output of postprocess stderr, -vv
                                      for full verbosity
                --help              - show help
```

## Examples
  
process main.js and generate output to stdout
```
jsew test/case-1/main.js
```
  
full verbose, parse main.js to script.js file, pipe output through uglify
```
jsew -vv -p 'uglifyjs --screw-ie8 --lint' -o script.js test/case-1/main.js
```

list (index) component files which would be used for output generation
```
jsew -i test/case-1/main.js
```
  
change directory, build output file from four separate compoents and uglify it
```
jsew -d test/case-2 -p uglifyjs -b a.js -a c.js -c copy b.js
```

Rewrite me to Node.JS please.

## License

[the MIT license](https://github.com/twbs/bootstrap/blob/master/LICENSE)
