# Matter

Matter is my idea of an ideal PHP framework. It's a personal experiment: I'm building it to find out what a PHP
framework looks like when it's designed for modern PHP from the start, rather than shaped by how things once had to
be done.

This repository is Matter's record: the decisions I've made, the designs I'm proposing, and, once something is
built, how it works.

## What I'm aiming for

Clean, well-structured code, and better solutions to the problems a framework has to solve, in ways that work for
me. Where I think the usual answer is wrong, Matter tries another.

## Reading this record

It's written for people who know PHP web development and at least one full-stack framework, such as Laravel or
Symfony. Concepts from that world aren't explained. Matter's own terms are, in [`GLOSSARY.md`](GLOSSARY.md), and
each document links them where they're used.

Matter has one author, so documents are written in the first person.

- **`rfc/`** proposes how something should work, and has a page in the spec once built.
- **`adr/`** records a decision that constrains designs across the spec.
- **`spec/`** describes how Matter works right now. It appears once something is built.
- **`ref/`** holds research and background material, never normative.

[`INDEX.md`](INDEX.md) lists every document and how they relate. It's generated, so don't edit it by hand. Read
[`PROCESS.md`](PROCESS.md) before adding anything.
