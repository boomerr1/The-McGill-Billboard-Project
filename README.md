# The McGill Billboard Project

## Index
Most users will want to download the index to the dataset:

* [billboard-2.0-index.csv](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/billboard-2.0-index.csv)

The index is a CSV files with the following columns:

* id, the index for the sample entry;
* chart_date, the date of the chart for the entry;
* target_rank, the desired rank on that chart;
* actual_rank, the rank of the song actually annotated, which may be up to 2 ranks higher or lower than the target rank [1, 2];
* title, the title of the song annotated;
* artist, the name of the artist performing the song annotated;
* peak_rank, the highest rank the song annotated ever achieved on the Billboard Hot 100; and
* weeks_on_chart, the number of weeks the song annotated spent on the Billboard Hot 100 chart in total.

Sample entries for which we were unable to obtain audio or an annotation also appear in the index, but with the id, chart_date, and target_rank columns exclusively.

## Complete Annotations
The complete annotations – chords, structure, instrumentation, and timing – are available from these links:

* [billboard-2.0-salami_chords.tar.xz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-salami_chords.tar.bz2](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-salami_chords.tar.gz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

The annotations files are named salami_chords.txt to reflect the fact that they contain both SALAMI-style structural annotations and the McGill Billboard chord annotations.

Each annotation begins with a header including the title of the song (prefixed by # title:), the name of the artist (prefixed by # artist:), the metre (prefixed by # metre:), and the tonic pitch class of the opening key (prefixed by # tonic:). Similar metre and tonic comments may also appear in the main body of the annotations, corresponding to changes of key or metre. In some cases, there is no obviously prevailing key, in which case the tonic pitch class is denoted ?.

The main body of each annotation consists of a single line for each musical phrase or other sonic element at a comparable level of musical structure. Each line begins with a floating-point number denoting the timestamp of the beginning of the phrase (in seconds) followed by a tab character. There are special lines for silence at the beginning and end of the audio file and a special line for the end of the piece. The other lines continue with a comma-separated list of elements among the following.

* __Capital letters__, possibly followed by an arbitrary number of primes (apostrophes), designate high-level musical structures. They appear at the beginning of each high-level musical segment and are presumed to continue until the next appearance of a capital letter. When two letters match, the two high-level segments are musically similar. Other than denoting similarity, the letters themselves have no intrinsic meaning, but for the letter Z. Z denotes non-musical passages in the audio such as noise or spoken words.
* __Plain text strings__ denote more traditional names for musical structures, e.g., verse, chorus, and bridge. The vocabulary was semi-restricted, but annotators had the freedom to use whatever terms they felt were most appropriate for unusual contexts.
* __Chord annotations__ appear as series of bars flanked by pipes (|). A phrase may by followed by an x and an integer, which means that the phrase is repeated that number of times. A phrase may also be followed by an arrow (->), which is a musicological hint that the phrase is musically elided into the following phrase.
* __Leading instruments__ are noted in songs where there is a notable deviation from the norm of a leading vocal throughout the entire song. They appear as text strings preceded by a left parenthesis (() in the segment where the instrument comes to prominence and as text strings succeeded by a right parenthesis ()) in the segment where that instrument fades from prominence. If an instrument is prominent for a single segment only, its name appears with both left and right parentheses.

More detail on the structural annotations is available from Smith et al. [3]. The McGill Billboard annotations replace the lower level of structural annotations from this reference (lowercase letters) with chord annotations.

The chord annotations are simplified to the beat level. All chord symbols follow the standard that Harte et al. presented at ISMIR 2005 and used in MIREX ever since [4], with a few additions to the shorthand to facilitate the richness of these annotations: 1 for unharmonised bass notes, 5 for power chords, and sus2, maj11, 11, min11, maj13, 13, and min13 for the corresponding chords in traditional jazz notation. An additional pseudo-chord type of 1 denotes bass notes with no chord on top. To save space, repeated chords are denoted with a dot instead of the full chord name. To further save space, bars containing a single chord on all beats list the chord symbol only once; likewise, in quadruple metres (4/4 or 12/8), bars with only two chords and the change on the third beat list those two chords with no dots. For brief changes of metre, the metre may appear in parentheses at the beginning of the bar rather than as a full metre comment.

Two non-chord symbols may appear within bars. For passages that were too musically elaborate to merit beat-level chord annotations, annotators sometimes filled the bar with an asterisk (\*). For brief pauses of arbitrary length (often a single beat), annotators added a bar with the special annotation &pause.

Bas de Haas has written Haskell tools for parsing and manipulating the McGill Billboard annotations [5], which are available from Hackage:

* http://hackage.haskell.org/package/billboard-parser/


## LAB Files (MIREX Style)
Users who are only interested in automatic chord recognition may prefer to download HTK-style LAB files for the chord annotations instead, which contain only onset times, offset times, and the chord labels, as used for the audio chord estimation task in MIREX:

* [billboard-2.0.1-lab.tar.xz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0.1-lab.tar.bz2](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0.1-lab.tar.gz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

Note that only the first chord of each phrase was time-aligned by a human. The timings for all other chords are linearly interpolated assuming a constant tempo for each phrase. This constant-tempo assumption is remarkably robust for the McGill Billboard sample: less than one percent of all possible eighth-note positions (tatums) in the sample are more then 10 percent faster or slower than the average tempo of the songs to which they belong [5].

For convenience, we also have LAB files with chord labels simplified to the vocabularies that will be used for evaluating chord estimation in MIREX 2013:

* [billboard-2.0.1-mirex.tar.xz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0.1-mirex.tar.bz2](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0.1-mirex.tar.gz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

## Audio features
Although we cannot distribute the original audio due to copyright, we have two feature sets available. Users interested in chord recognition may want the non-negative-least-squares chroma vectors and tuning estimates from the Chordino VAMP plugin [6]:

* [billboard-2.0-chordino.tar.xz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-chordino.tar.bz2](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-chordino.tar.gz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

These archives contain bothchroma.csv and tuning.csv for each annotated single. We used the default settings for the plugin with the exception for a rolloff of 1 percent, the plugin authors’ recommendation for pop music.

We have updated the old echonest.jsons with the more up to date Spotify API analyses:

* [billboard-2.0-spotify.tar.xz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-spotify.tar.bz2](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-spotify.tar.gz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

Essentia/AcousticBrainz features:

* [billboard-2.0-essentia.tar.xz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-essentia.tar.bz2](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

* [billboard-2.0-essentia.tar.gz](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/)

If you are interested in audio features other than these, please contact us. So long as the features are non-invertible and the computational load is sane, we are happy to provide custom features upon request.


