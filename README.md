# Discoverio - 30 Juin 2023

![logo discoverio](markdown/img/Logo/PNG/logo_vertical_original.png)

## Requirements

- nodejs
- npm
- [reveal-md](https://github.com/webpro/reveal-md)

## Tools

### Diagrams

All the diagrams has been generated with [app.diagrams.net](https://app.diagrams.net/) application.

### Presentation

We use [reveal-md](https://github.com/webpro/reveal-md) to generate the presentation.

#### Installation

```bash
pacman -Sy node npm
npm install -g npm@latest
npm -v

npm install -g reveal-md
```

## Run locally

### Server mode

**reveal-md** have a server version.

#### Docker

```bash
docker run --rm -p 1948:1948 -p 35729:35729 -v ${PWD}:/slides webpronl/reveal-md:latest ./markdown --watch --css ./style.css --listing-template ./listing.html
```

### Export to PDF

Run the server.

```bash
docker run --rm -p 1948:1948 -p 35729:35729 -v ${PWD}:/slides webpronl/reveal-md:latest ./markdown --watch --css ./style.css --listing-template ./listing.html
```

Export the slides.

```bash
mkdir exports;
docker run --rm -t --net=host -v $PWD:/slides astefanutti/decktape -s 1024x1024 "http://localhost:1948/presentation.md#/" ./exports/presentation.pdf
```

### Convert to HTML files

```bash
docker run --rm -v ${PWD}:/slides webpronl/reveal-md:latest ./markdown --static public/ --static-dirs=markdown/img/ --css markdown/style.css --listing-template markdown/listing.html
```

This command convert the markdowns to HTML files.
The convertion generates a [public](public/) directory.

## Usage

To display the speaker notes update the [reveal.json](./reveal.json) configuration file.
