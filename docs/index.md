# Bienvenida!

## Fork and clone the main repo in version 3.9

### Create your branch

## Building

```
./configure --with-pydebug
make -j2 -s
```

## Modifying

### Direct statements

``` title="python.gram" linenums="1"
small_stmt:

| 'pass' { _Py_Pass(EXTRA) } -> | ('pass' | 'pasar') { _Py_Pass(EXTRA) }
```

### Referenced statements

``` title="python.gram" hl_lines="8"
small_stmt:
| &'return' return_stmt -> | &('return' | 'retornar') return_stmt

...

return_stmt[stmt_ty]:
    | 'return' a=[star_expressions] { _Py_Return(a, EXTRA) }
    | 'retornar' a=[star_expressions] { _Py_Return(a, EXTRA) }
```


### Regenerate the parser

```
make regen-pegen
```

### Recompile

```
./configure --with-pydebug
make -j2 -s
```

### Try it!

```
./python

def foo():
    pasar

foo()
```