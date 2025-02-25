## Runtime Symbol Bindings

The runtime bindings exported by the prelude are all externs collected in nested modules,
which allows for easy reuse in custom languages.

### Runtime [phi=0] Bindings

This includes the `<runtime>` prelude module, which is composed by the `<r5rs-runtime>` and
`<host-runtime>` modules.

#### `<r5rs-runtime>`

Defines the following symbols as externs:
```
    ;; 6.1 equivalence
    eq? eqv? equal?
    ;; 6.2 numbers
    number? complex? real? rational? integer?
    exact? inexact?
    = < > <= >=
    zero? positive? negative? odd? even?
    max min
    + * - /
    abs quotient remainder modulo gcd lcm
    floor ceiling truncate round
    numerator denominator rationalize
    exp log sin cos tan asin acos atan
    sqrt expt
    make-rectangular make-polar real-part imag-part magnitude angle
    exact->inexact inexact->exact
    number->string string->number
    ;; 6.3 other data types
    ;;  6.3.1 bool
    not boolean?
    ;;  6.3.2 pairs
    pair? cons car cdr set-car! set-cdr!
    caar cadr cdar cddr
    caaar cadar caadr caddr
    cdaar cddar cdadr cdddr
    caaaar caadar caaadr caaddr
    cadaar caddar cadadr cadddr
    cdaaar cdadar cdaadr cdaddr
    cddaar cdddar cddadr cddddr
    null? list? list length append reverse list-tail list-ref
    memq memv member
    assq assv assoc
    ;;  6.3.3 symbols
    symbol? symbol->string string->symbol
    ;;  6.3.4 characters
    char? char=? char<? char>? char<=? char>=?
    char-ci=? char-ci<? char-ci>? char-ci<=? char-ci>=?
    char-alphabetic? char-numeric? char-whitespace?
    char-upper-case? char-lower-case?
    char->integer integer->char
    char-upcase char-downcase
    ;;  6.3.5 strings
    string? make-string string
    string-length string-ref string-set!
    string=? string-ci=?
    string<? string>? string<=? string>=?
    string-ci<? string-ci>? string-ci<=? string-ci>=?
    substring string-append
    string->list list->string
    string-copy string-fill!
    ;;  6.3.6 vectors
    vector? make-vector vector
    vector-length vector-ref vector-set!
    vector->list list->vector
    vector-fill!
    ;; 6.4 control
    procedure? apply
    map for-each
    force
    call-with-current-continuation
    call-with-values values
    dynamic-wind
    ;; 6.5 eval
    eval interaction-environment scheme-report-environment
    ;; 6.6 i/o
    call-with-input-file call-with-output-file
    input-port? output-port?
    current-input-port current-output-port
    with-input-from-file with-output-to-file
    open-input-file open-output-file
    close-input-port close-output-port
    read read-char peek-char
    eof-object? char-ready?
    write display newline write-char
    load
```

#### `<host-runtime>`

Defines the following symbols as externs:
```
    immediate?
    finite? infinite? nan?
    1+ 1- fx+ fx1+ fx- fx1- fx* fx/
    fixnum? nonnegative-fixnum?
    fxzero? fxpositive? fxnegative? fxodd? fxeven?
    fixnum->flonum
    fxmax fxmin fxabs fxnot fxand fxior fxxor fxmodulo
    fxbit-set? fxarithmetic-shift fxarithmetic-shift-left fxarithmetic-shift-right
    fxshift
    fx< fx<= fx= fx>= fx>
    flonum?
    fl+ fl- fl* fl/ fl< fl<= fl= fl>= fl>
    flzero? flpositive? flnegative?
    flnan? flinfinite? flfinite? flinteger?
    flmax flmin
    arithmetic-shift bitwise-and bitwise-ior bitwise-xor bitwise-not
    bitwise-merge integer-length
    box? box unbox set-box!
    make-list cons*
    foldl foldr andmap ormap filter filter-map iota last last-pair
    memf assgetq assgetv assget find
    list-set list-set!
    remove1 remq remv remf
    pgetq pgetv pget
    subvector subvector->list subvector-fill!
    vector-copy!
    vector-map vector-for-each vector-copy vector-copy! vector-append
    true true? false void void? eof-object identity
    dssl-object? dssl-key-object? dssl-rest-object? dssl-optional-object?
    values-count values->list
    make-hash-table make-hash-table-eq make-hash-table-eqv
    hash-table?
    hash->list hash->plist
    list->hash-table list->hash-table-eq list->hash-table-eqv
    plist->hash-table plist->hash-table-eq plist->hash-table-eqv
    hash-length hash-ref hash-get hash-put! hash-remove! hash-update! hash-key?
    hash-find hash-for-each hash-map hash-fold
    hash-keys hash-values
    hash-copy hash-copy!
    hash-merge hash-merge!
    hash-clear!
    eq?-hash eqv?-hash equal?-hash
    uninterned-symbol? interned-symbol? string->uninterned-symbol
    gensym make-symbol make-uninterned-symbol symbol-hash
    keyword? uninterned-keyword? interned-keyword? keyword-hash
    string-map string-for-each
    string-copy string-copy! substring-fill!
    string->bytes substring->bytes bytes->string
    string->vector vector->string
    string-concatenate
    string-index string-rindex
    string-split string-join string-empty? string-prefix?
    string->keyword keyword->string make-uninterned-keyword
    symbol->keyword keyword->symbol
    ;; MOP
    type-descriptor?
    struct-type?
    class-type?
    make-struct-type
    make-struct-predicate
    make-struct-field-accessor
    make-struct-field-mutator
    make-struct-field-unchecked-accessor
    make-struct-field-unchecked-mutator
    struct-field-ref
    struct-field-set!
    unchecked-field-ref
    unchecked-field-set!
    make-class-type
    make-class-predicate
    make-class-slot-accessor
    make-class-slot-mutator
    make-class-slot-unchecked-accessor
    make-class-slot-unchecked-mutator
    class-slot-ref
    class-slot-set!
    class-slot-offset
    unchecked-slot-ref
    unchecked-slot-set!
    object? object-type
    struct-instance? class-instance?
    direct-instance? direct-struct-instance? direct-class-instance?
    make-object
    struct-copy
    struct->list class->list
    make-struct-instance
    make-class-instance
    struct-instance-init!
    class-instance-init!
    slot-ref slot-set!
    call-method
    bind-method! bind-specializer!
    seal-class!
    method-ref direct-method-ref bound-method-ref
    checked-method-ref checked-bound-method-ref
    find-method
    next-method call-next-method
    struct-subtype? class-subtype?
    ;; write-env style
    write-style
    ;; control
    current-error-port
    make-promise promise?
    make-parameter call-with-parameters
    ;;call-with-prompt abort!
    with-unwind-protect
    current-exception-handler
    with-exception-handler
    with-catch
    error raise
    exception? error-object?
    error-message error-irritants error-trace
    display-exception
    ;; OS
    exit getenv setenv
    current-directory create-directory create-directory*
    delete-file copy-file rename-file
    delete-directory directory-files
    delete-file-or-directory
    file-exists? file-newer? file-type
    path-expand path-normalize
    path-extension path-strip-extension
    path-directory path-strip-directory
    path-strip-trailing-directory-separator
    ;; reader
    AST? AST::t make-AST AST-e AST-source
    read-syntax read-syntax-from-file
    source-location? source-location-path? source-location-path
    make-syntax-error syntax-error?
    read-line read-all
    ;; string and vector moves
    vector-concatenate subvector-move! vector-shrink!
    string-concatenate substring-move! string-shrink!
    ;; string I/O
    read-substring write-substring
    open-input-string open-output-string get-output-string
    call-with-input-string with-input-from-string
    call-with-output-string with-output-to-string
    ;; bytes
    u8vector? u8vector
    make-u8vector u8vector-length u8vector-ref u8vector-set!
    u8vector->list list->u8vector
    u8vector-fill! u8vector-shrink!
    u8vector-copy u8vector-copy! u8vector-append
    subu8vector subu8vector-fill! subu8vector-move!
    u8vector-concatenate
    object->u8vector u8vector->object
    ;; bytes I/O
    read-subu8vector write-subu8vector
    open-input-u8vector open-output-u8vector get-output-u8vector
    call-with-input-u8vector with-input-from-u8vector
    call-with-output-u8vector with-output-to-u8vector
    ;; generic I/O
    displayln display*
    ;; formerly ##max-char
    max-char-code
    ;;flush-output-port
    ;; etc...
    absent-obj   ; gambit api missing optional parameter
    absent-value ; unbound hash reference atom
    ;; Module loading
    load-module
    ;; keyword argument dispatch
    keyword-dispatch keyword-rest
    ;; gerbil specifics
    gerbil-version-string gerbil-system-version-string system-version
    ;; system type information
    gerbil-system system-type
    ;; voodoo doll
    gerbil-runtime-smp?
    ;; expander loading for executables
    gerbil-load-expander!
    ;; our home
    gerbil-home

    ;; concurrency primitives
    spawn spawn/name spawn/group spawn-actor spawn-thread
    thread-local-ref thread-local-get thread-local-set! thread-local-clear!
    unhandled-actor-exception-hook-set!

    thread? actor-thread?
    thread-sleep! thread-join! thread-send thread-receive
    thread-specific thread-specific-set!
    make-thread thread-start! thread-yield!
    thread-name
    current-thread

    thread-thread-group
    thread-group?
    thread-group-name
    current-thread-group

    make-mutex mutex? mutex-lock! mutex-unlock! with-lock with-dynamic-lock
    make-condition-variable condition-variable?
    condition-variable-signal!
    condition-variable-broadcast!

    ;; continuation primitives
    continuation? continuation-capture continuation-graft continuation-return
    display-continuation-backtrace

    ;; time objects
    current-time
    time?
    time->seconds
    seconds->time

    ;; port utilities
    port? close-port force-output
    read-all
    read-line
    peek-char
    read-u8 peek-u8 write-u8
    char-ready?

    read-string write-string
    read-u8vector write-u8vector

    ;; misc r7rs procedures
    list-copy list-set!
    string-downcase string-upcase
    exact-integer?
    exact inexact
    exact-integer-sqrt
```

Also defines the following aliases:
```
  (define-alias transcript-on void)
  (define-alias transcript-off void)
  (define-alias car-set! set-car!)
  (define-alias cdr-set! set-cdr!)
  (define-alias box-set! set-box!)
  (define-alias call/cc         call-with-current-continuation)
  (define-alias call/esc        call-with-escape)
  (define-alias call/values     call-with-values)
  (define-alias call/parameters call-with-parameters)

```

### Syntax [phi=1] Bindings

The bindings include `<runtime>` and `<expander-runtime>`, which contains symbols
defined by the expander.

#### `<expander-runtime>`

Defines the following symbols as extern:
```
    ;; syntax and friends
    raise-syntax-error syntax-error?
    identifier? identifier-list? free-identifier=? bound-identifier=?
    datum->syntax syntax->datum syntax-e syntax->list
    genident gentemps
    stx-identifier
    stx-boolean? stx-keyword? stx-char? stx-number? stx-fixnum? stx-string?
    stx-null? stx-pair? stx-pair/null? stx-list?
    stx-box? stx-vector? stx-datum?
    stx-eq? stx-eqv? stx-equal? stx-false?
    stx-e stx-source stx-wrap-source
    stx-car stx-cdr stx-length
    stx-for-each stx-map stx-foldl stx-foldr stx-reverse
    stx-last stx-last-pair stx-list-tail stx-list-ref
    stx-andmap stx-ormap
    stx-plist? stx-getq
    macro-expand-syntax
    macro-expand-syntax-case
    syntax-pattern? syntax-local-pattern?
    make-syntax-pattern syntax-pattern-id syntax-pattern-depth
    syntax-check-splice-targets
    syntax-split-splice
    underscore? ellipsis?
    check-duplicate-identifiers
    ;; core expander -- user api
    current-expander-context
    current-expander-marks
    current-expander-path
    current-expander-phi
    current-module-reader-path
    current-module-reader-args
    local-context? top-context? module-context? prelude-context?
    expander-context-id  module-context-ns
    make-local-context
    eval-syntax core-expand core-expand-head core-expand-expression+1
    import-module eval-module
    core-library-module-path? core-resolve-library-module-path
    core-resolve-module-path
    core-quote-syntax
    core-identifier=? core-identifier-key
    core-apply-expander
    syntax-local-introduce syntax-local-rewrap syntax-local-unwrap
    syntax-local-e syntax-local-value
    resolve-identifier core-resolve-identifier
    binding? binding-id
    runtime-binding? top-binding? module-binding? extern-binding?
    syntax-binding? syntax-binding-e
    alias-binding? alias-binding-e
    import-binding? import-binding-e
    expander? expander-binding? expander-e expander-binding-e
    feature-expander?
    user-expander? make-user-expander
    user-expander-context user-expander-phi
    import-expander? make-import-expander
    export-expander? make-export-expander
    module-import? make-module-import
    module-import-source module-import-name module-import-phi
    module-import-weak?
    module-export? make-module-export
    module-export-context module-export-key module-export-phi
    module-export-name module-export-weak?
    import-set? import-set-source import-set-phi import-set-imports
    export-set? export-set-source export-set-phi export-set-exports
    core-resolve-module-export
    core-module-export->import
    core-expand-import-source
    core-expand-export-source

```

### More Gambit Symbols

There are more symbols provided by the Gambit runtime, which you may find useful
in systems programming. These are not defined in the core prelude by default to
avoid namespace bloat. Instead, they are defined in the `:gerbil/gambit` module,
which you can import to access the totality of Gambit runtime bindings:
``` scheme
(import :gerbil/gambit)
```

Note that the module only exports extern symbols and some aliases;
check the Gambit Manual for documentation on the totality of Gambit
runtime symbols.
