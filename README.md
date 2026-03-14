# pharscript

Creates a PHP wrapper script that bootstraps an embedded PHAR archive.

## Usage

Generate a standalone PHP launcher from a PHAR:

```bash
php pharscript.php app.phar app.php
```

Optional mode flags:

```bash
php pharscript.php --in-memory app.phar app.php
php pharscript.php --temp-file app.phar app.php
```

If no mode flag is provided, the default is memory-first with temp-file
fallback.

The generated `app.php`:

- Contains a PHP launcher stub.
- Uses `__halt_compiler()` to mark the boundary.
- Appends the raw PHAR binary after the stub.
- Loads the embedded PHAR from memory when possible.
- Falls back to a temp file only when memory loading is unavailable.
