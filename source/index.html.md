---
title: Otterly data structure

language_tabs: # must be one of https://git.io/vQNgJ
  - json

toc_footers:
  - <a> version 1.0 </a>
  - <a> updated 20/01/2019 </a>

includes:
  - users
  - dishes
  - restaurants
  - carts
  - orders

search: true
---

# Introduction

Welcome to the Otterly data structure document. This page outlines the different classes and data-structure utilised in the firestore backend for Otterly.

# Authentication

Autorization takes place in the context of firebase authentication. Primarily we use three auth providers - Google, Facebook, and Phone authentication. There is no password involved.

More info on firebase authentication can be found in the [official docs] (https://https://firebase.google.com/docs/auth/).

The authentication details are stored automatically in the firebase authentication database, and some details are correspondingly stored in the [`users`](#users) collection.





