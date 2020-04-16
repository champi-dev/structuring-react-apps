<a href="https://www.buymeacoffee.com/2kaTCuq" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>

Clone the [companion repo](https://github.com/champi-dev/structuring-react-apps-companion) to follow along.

> ui kit disclaimer:
>
> I'll use [this paid ui kit](https://www.holomusic.co/) for the entire
> series but it's not necessary for you to buy it though since I'll be
> translating it to it's equivalent css.

# Structuring React Apps

## Goal

To thoroughly expose the thought process involved in every step related to the development of a complex React Project.

## What I mean by complex

A complex React Project is one that:

- Has to enforce linting/formatting rules to a development team.
- Needs to manage styles according to a UI style guide.
- Does not use an UI library but rather has it's own ui components written from scratch.
- Has container screens that need to share data with many children components.
- Manages and parses data coming from a web server.
- Handles different permissions in the app based on user role (e.g. private routes).
- Has support for different languages.
- Has unit tests to verify correctness of both UI logic (i.e. containers/components) and Business Data logic (i.e. redux).

## Business problem definition

We want to create a music streaming platform where:

### Listeners can:

- Find independent artists
- Save artists as favorites
- Listen to their music
- Leave comments on tracks

### Artists can:

- Submit their music/art
- Reply to user comments
- See stats related to streams

### An admin can:

- Enable artists into the platform
- See overall stats

## Table of Contents

- [Get started](./1.get-started/README.md)
- [Building UI components](./2.building-ui-components/README.md)
