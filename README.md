# filemagic

**A robust Python API for libmagic, the library behind the Unix `file` command.**  
Easily determine file types, MIME types, and encodings in Python—cross-platform and across Python 2 & 3.

---

## Overview

filemagic is a Python library that provides a high-level interface to [libmagic](https://darwinsys.com/file/)—the engine behind standard Unix file identification tools. With filemagic, you can detect file types and encodings directly from Python, based on magic numbers and internal file structure (not just filename extensions). The project also offers a command-line utility compatible with the classic `file` command, and extensive documentation and test coverage.

---

## Features

- **File type detection:** Identify files using magic numbers.
- **MIME type & encoding:** Retrieve both type (e.g., `text/x-python`) and encoding (e.g., `us-ascii`).
- **Context manager support:** Safe resource management with `with` statements.
- **Cross-version:** Works on Python 2.6+, 3.x, and PyPy.
- **Command-line tool:** Scriptable interface for shell or automation pipelines.
- **Rich documentation:** Sphinx docs included.
- **Thorough testing:** Unit tests for core and edge-case behavior.
- **Open source:** Licensed under the Apache Software License.

---

## Installation

Install with pip (requires `libmagic` installed on your system):
pip install filemagic

Or from source:

python setup.py install


**Development dependencies** (for testing and docs):

pip install -r requirements/development.txt


---

## Requirements

- Python 2.6, 2.7, 3.2, 3.3, or PyPy
- `libmagic` C library (must be installed system-wide)
- [ctypes](https://docs.python.org/3/library/ctypes.html) (bundled with Python standard library)

---

## Usage

### Python API

import magic

with magic.Magic() as m:
description = m.id_filename('setup.py')
print(description) # e.g., "ASCII text"

mime = magic.Magic(flags=magic.MAGIC_MIME_TYPE).id_filename('setup.py')
print(mime)  # e.g., "text/x-python"


Or use buffer (in-memory):

with magic.Magic() as m:
desc = m.id_buffer(b'GIF89a...')
print(desc)


### Command-Line Interface

After installation, you can run:

python -m magic <options> filename


See all options with `--help`.

---

## Documentation

Full documentation is available in `docs/` and can be built using [Sphinx](https://www.sphinx-doc.org/):

cd docs
make html # builds docs in _build/html/


Or visit the hosted docs at:  
http://filemagic.readthedocs.org

---

## Testing

Run the test suite using:

python test_magic.py


Coverage is measured and reported via `coverage` and `coveralls` (see `.travis.yml` for details).

---

## Contributing

- Fork, branch, and submit pull requests on GitHub.
- Please add new tests for new features or bug fixes.
- Conformance to PEP8 and flake8 is recommended (`pip install flake8`).

---

## License

Apache Software License (ASL). See `LICENSE` for full terms.

---

## Credits

- Original author: Arjun (arjun@gmail.com)
- Inspired by Unix `file` tool and the libmagic project.
- Contributors: See `CONTRIBUTORS`
- Special thanks: [Aaron Iles](mailto:aaron.iles+travis-ci@gmail.com) for CI and testing infra.

---

## CI Status

[![Build Status](https://travis-ci.org/yourusername/filemagic.svg?branch=master)](https://travis-ci.org/yourusername/filemagic)
[![Coverage Status](https://coveralls.io/repos/github/yourusername/filemagic/badge.svg?branch=master)](https://coveralls.io/github/yourusername/filemagic?branch=master)

---

## Further Reading

- [libmagic home](https://darwinsys.com/file/)
- [Sphinx documentation](https://www.sphinx-doc.org/)



