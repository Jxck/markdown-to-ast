# markdown-to-ast [![Build Status](https://travis-ci.org/textlint/markdown-to-ast.svg)](https://travis-ci.org/textlint/markdown-to-ast)

Parse Markdown to AST with location info.

This library is not parser itself, it dependent on [wooorm/remark](https://github.com/wooorm/remark).

> Markdown -> remark -> markdown-to-ast -> TxtNodes

The AST consists of `TxtNode`s.
A `TxtNode` of the AST has following properties:

- `loc` - Nodes have line and column-based location info.
- `range` - Nodes have an index-based location range (array).
- `raw` - Node have a `raw` text.

The interface defined as [txtnode.d.ts](typing/txtnode.d.ts).

This library is a part of [textlint/textlint](https://github.com/textlint/textlint "textlint/textlint").


## DEMO

[![screenshot](http://monosnap.com/image/0fqi1UF7yOv89nxJPaDWtvyqERaM49.png)](http://azu.github.io/markdown-to-ast/example/)

[Online Parsing Demo](http://azu.github.io/markdown-to-ast/example/) provide markdown to AST on-the-fly.

## Installation

```
npm install markdown-to-ast
```

## Usage

```sh
var parse = require("markdown-to-ast").parse;
var markdown = "It's a *text*";
var AST = parse(markdown);
/*
{
    "type": "Document",
    "children": [
        {
            "type": "Paragraph",
            "children": [
                {
                    "type": "Str",
                    "value": "It's a ",
                    "loc": {
                        "start": {
                            "line": 1,
                            "column": 0
                        },
                        "end": {
                            "line": 1,
                            "column": 7
                        }
                    },
                    "range": [
                        0,
                        7
                    ],
                    "raw": "It's a "
                },
                {
                    "type": "Emphasis",
                    "children": [
                        {
                            "type": "Str",
                            "value": "text",
                            "loc": {
                                "start": {
                                    "line": 1,
                                    "column": 8
                                },
                                "end": {
                                    "line": 1,
                                    "column": 12
                                }
                            },
                            "range": [
                                8,
                                12
                            ],
                            "raw": "text"
                        }
                    ],
                    "loc": {
                        "start": {
                            "line": 1,
                            "column": 7
                        },
                        "end": {
                            "line": 1,
                            "column": 13
                        }
                    },
                    "range": [
                        7,
                        13
                    ],
                    "raw": "*text*"
                }
            ],
            "loc": {
                "start": {
                    "line": 1,
                    "column": 0
                },
                "end": {
                    "line": 1,
                    "column": 13
                }
            },
            "range": [
                0,
                13
            ],
            "raw": "It's a *text*"
        }
    ],
    "loc": {
        "start": {
            "line": 1,
            "column": 0
        },
        "end": {
            "line": 1,
            "column": 13
        }
    },
    "range": [
        0,
        13
    ],
    "raw": "It's a *text*"
}
*/
```

The interface of a node on AST is defined as [txtnode.d.ts](typing/txtnode.d.ts).

If you want to know real use-case, please see [textlint/textlint](https://github.com/textlint/textlint "textlint/textlint").

## Tests

```
npm test
```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

MIT
