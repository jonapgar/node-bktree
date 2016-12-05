Damerau-Levenshtein BK Tree
===========

A JavaScript implementation of a Burkhard-Keller Tree (BK-Tree) that uses either the Levenshtein or Damerau-Levenshtein algorithm to calculate the distance between strings.

Install
-------

    npm install bktree-damlev

Usage
-----

A basic example without passing any options. By default the Levenshtein algorithm is used:

```javascript
var bktree = require('bktree');
var terms = [
  'accommodate', 'accommodation', 'achieve', 'across',
  'aggression', 'aggressive', 'apparently', 'appearance',
  'argument', 'assassination', 'basically', 'beginning',
  'believe', 'bizarre', 'business', 'calendar',
  'caribbean', 'cemetery', 'chauffeur', 'colleague',
  'coming', 'committee', 'completely', 'conscious',
  'curiosity', 'definitely', 'dilemma', 'disappear',
  'disappoint', 'ecstasy', 'embarrass', 'environment',
  'existence', 'fahrenheit', 'familiar', 'finally',
  'fluorescent', 'foreign', 'foreseeable', 'forty',
  'forward', 'friend', 'further', 'gist',
  'glamorous', 'government', 'guard', 'happened',
  'harass', 'harassment', 'honorary', 'humorous',
  'idiosyncrasy', 'immediately', 'incidentally', 'independent',
  'interrupt', 'irresistible', 'knowledge', 'liaise',
  'liaison', 'lollipop', 'millennia', 'millennium',
  'neanderthal', 'necessary', 'noticeable', 'occasion',
  'occurred', 'occurrence', 'occurring', 'pavilion',
  'persistent', 'pharaoh', 'piece', 'politician',
  'portuguese', 'possession', 'preferred', 'preferring',
  'propaganda', 'publicly', 'really', 'receive',
  'referred', 'referring', 'religious', 'remember',
  'resistance', 'sense', 'separate', 'siege',
  'successful', 'supersede', 'surprise', 'tattoo',
  'tendency', 'therefore', 'threshold', 'tomorrow',
  'tongue', 'truly', 'unforeseen', 'unfortunately',
  'until', 'weird', 'wherever', 'which'
  ];

// Build the tree
var tree = new bktree(terms);

// Get correctly spelled words at distance <= 3
var r = tree.query('refered', 3);
// [ 'referred', 'preferred' ]

// Return closest
var r = tree.query('refered', 3, 1);
// [ 'referred' ]
```

`bktree` can be passed the following options in a second parameters:

- transposition - Uses Damerau–Levenshtein algorithm instead of the Levenshtein algorithm.
- details - Returns matching terms and their distance (rather than just the terms).
- path - If each term is a object, and the string to compare is a member of that object.

For example:

```
var terms = [
  {word: 'accommodate'},
  {word: 'accommodation'}
];
var tree = new bktree(terms, {transposition: true, details: true, path: 'word'});
```

Credits
-------

Based on [node-bktree](https://github.com/jonahharris/node-bktree) by Jonah H. Harris.

Changes by Thomas Baron.
