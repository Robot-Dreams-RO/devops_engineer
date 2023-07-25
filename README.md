# Introduction to DevOps documentation

Documentation is made using ``Sphinx``, to build it:

1. Create and init a virtual environment

    ```bash
    python3.11 -m venv venv
    source venv/bin/activate
    ```

2. Install Python dependencies

    ```bash
    pip install -r requirements.txt
    ```

3. Build documentation

    ```bash
    make clean html
    ```

4. To read the documentation - open explorer.exe, change the directory to ``build``, then ``index.html``.

    ```bash
    explorer.exe .
    ```

To have documentation available on GitHub pages you need to copy the files from ``build/html`` to docs (limitation from gh-pages) then will pick the ``index.html``

```bash
rm -rf docs/* && cp -R build/html/* docs/ && touch docs/.nojekyll
```

To build the documentation for ``pdf`` or ``epub``, run

```bash
make pdf
# or
make epub
```
