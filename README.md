lmNotation
==========

> ***This guide is version 0.1 of the lmNotation standard.***

**In short**: Leitmotif Notation, a compact way to write short phrases of music
in a key-relative, intervallic format. Much of its syntax is inspired by solfège
and the [Lilypond file format](http://lilypond.org/).

## What is lmNotation?

**lmNotation**, or *Leitmotif Notation*, is a way of writing phrases of music
(or *motifs*) in a way that is *key-relative*, or without key. It assumes the
following holds true:

* The intended phrase adheres (at least loosely) to the diatonic scale, or is a
derivative/relative of the diatonic scale
* *[More to be added...]*

It shares slight similarities with [LilyPond notation](http://lilypond.org/),
although it is less strict in that all notes are relative to a relative tonic
center.

For example, where in traditional notation programs, a key of C major would be
defined, lmNotation only requires that the motif contain a tonic, centered on
the solfège `do`.

## Examples

As examples are often the best way to dive into a new concept, let's begin with
a couple basic phrases, and example how they can be expressed in lmNotation.

### Example One: Diatonic Major Scale

A typical diatonic major scale in 4/4 time would be written thusly:

    {4/4|do4 re4 mi4 fa4 sol4 la4 ti4 do4}

There are several basic features to note:

1. Each *motif* begins and ends with curly braces: `{ }`.
2. The first section of a motif is the time signature. In this example, the time
signature in this example is 4/4 time.
3. A pipe ("`|`") separates the time signature with the next section.
4. This next section contains the actual notes of the motif.
	* Each note is separated by a comma
	* Each note contains two pieces of information, a solfège representation of
	the note, and its length, relative to the time signature defined in the
	previous section.
5. The note length behaves much like you would expect. A `4` in 4/4 time is a
typical quarter note, and is held for exactly one beat.

A defining feature of lmNotation is the fact that every motif is key-relative.
It differs from traditional notation methods in that a motif can be written
without a key in mind, and can be transposed at will when needed. Other notation
software (e.g. LilyPond, or Sibelius) depend on having a discrete key signature,
which means that later transposition requires processing and translation.

### Example Two: Non-Diatonic Scales

Nothing stops you from writing other motifs in other scale system. Here is a
major pentatonic scale:

    {4/4|do4 re4 mi4 sol4 la4 do4 la4 sol4 mi4 re4 do1}

... and a minor pentatonic scale:

	{4/4|la4 do4 re4 mi4 sol4 la2.}
	or...
	{4/4|do4 mey4 fa4 sol4 tey4 do2.}

This last example also introduces the dot, which, like LilyPond notation,
behaves much like a dot in regular music. It extends the length of the note by
half of its base value. In the above case, a half note (`2`, or two beats, in
4/4 time) is held for three beats.

Also, the second minor pentatonic scale motif contains two accidentals:
`mey` and `tey`. Solfège containing the suffix `-ey` are lowered a half-step,
while solfège with the suffix `-i` are raised a half step (e.g. `si, ti`).

## Version History

* *[Proposed]* v0.1.1 &ndash; Additions to the lmNotation spec
	* Support for transpositions (`^sol` to transpose up a fifth, `_sol` to
	transpose down a fouth?)
	* Force upward/downward interval (`do2 'sol2` and `do2 ,fa2` &ndash; like
	LilyPond)
	* Triplets (how does LilyPond support triplets?)
* v0.1 &ndash; Codified the base format of an lmNotation motif
	* `{}` start/end
	* CSV for note separation
	* Example: `{4/4|do2 sol2 mi1}`
	* Accepted solfège: do, di/rah, re, ri/may, mi, fa, fi/say, sol, si/ley, la,
	li/tey, and ti