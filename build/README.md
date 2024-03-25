# Pymetangine docker image

## Single file mode

```
docker run --rm -v ./input:/input -v ./output:/output attilamester/pymetangine -i /input/file.orig -o /output/file.mutated
```

## Batch mode

```
docker run --rm -v ./input:/input -v ./output:/output attilamester/pymetangine -i /input -b -o /output
```