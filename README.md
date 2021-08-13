# TAO LTI 1.3 PHP framework documentation

> TAO LTI 1.3 PHP framework documentation, powered by [Github Pages](https://pages.github.com/).

## Hosted documentation

The documentation is available at [https://oat-sa.github.io/doc-lti1p3/](https://oat-sa.github.io/doc-lti1p3/).

## Development notes

### Theme documentation

The MkDocs theme documentation is available at [https://squidfunk.github.io/mkdocs-material/](https://squidfunk.github.io/mkdocs-material/).

### Previewing as you write

You can live preview changes as you write documentation by using the provided [Dockerfile](Dockerfile) (to avoid useless refresh triggers on Github Pages):

First build:

```shell
docker build -t doc-lti1p3 .
```

Then run:

```shell
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs doc-lti1p3
```

Finally, simply access [http://localhost:8000](http://localhost:8000). 