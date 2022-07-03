# mmm

___Public version of the repo. This version does not contain any code, only some file samples and a description.___

The full repository is available at this link (if you have the proper access): https://github.com/fabio-a-oliveira/mmm

## About

This project uses infinitepay transactions to create music.

We're using the transactions from the last hour to create a music clip in midi format. The clip will vary in length. It will contain two voices playing (somewhat) independent lines of music.

## How to listen

### 1. Live

Sadly, I couldn't get this to work live...

### 2. Listen to some pre-generated clips

You can download some clips from the `songs` folder or just clicking on these links:
- https://github.com/fabio-a-oliveira/mmm_public/raw/main/songs/mmm_2022_07_03-12_49_40.mid
- https://github.com/fabio-a-oliveira/mmm_public/raw/main/songs/mmm_2022_07_03-12_50_27.mid
- https://github.com/fabio-a-oliveira/mmm_public/raw/main/songs/mmm_2022_07_03-12_51_10.mid

If you can't execute them locally, you can view them online by using this online midi player: https://cifkao.github.io/html-midi-player/ 

## How transactions are reflected into the created music

Instead of taking some number from the transactions and translating it into notes (which usually just sounds like random music), we're taking a different approach here.

The idea is to generate music that makes a little sense (observing keys, chords, scales) and translating aspects of the transactions into things that we can actually hear and identify in the music.

Here's how some of the aspects from the transactions are translated into the generated song:

### 1. Number of transactions

The number of transactions will be reflected in the song's tempo. Running the code in a moment with a lot of transactions will generate faster music, while running it during a calmer period will create slower music.

### 2. Ratio of capture methods

The ratio of transactions with each capture method are reflected in the probability of choosing notes from the chord, from the diatonic scale or from outside the diatonic scale.

The ratio of emv transactions generates the probability of choosing notes from the chord (the most conservative choice).

The ratio of contactless transactions generates the probability of choosing notes from the diatonic scale (not the chord, but belonging to the key).

The ratio of other capture methods (pix, ecommerce, payment link) generate the probability of choosing notes from outside the key (the spicy notes).

As these other methods grow in participation, the music generated will become less predictable and more adventurous.

Since we're creating music in two channels, the first one uses the ratios in the approved transactions and the second channel uses the ratios in the other transactions.

### 3. Ratio of distinct card numbers to distinct merchants

At each 4 bars, the song will modulate to a new key. 

The ratio of distinct cardholders to distinct merchants will be used to determine the number of steps from the current key to take in the circle of fifths.

A lower ratio will result in more subtle changes in key. A higher ratio will result in changes that are more drastic.

A higher ratio is good in business terms. It means our costumers are making more sales to more distinct people. This will be translated into spicier tunes.

### 4. Approved amount

At each bar, the chord will be changed to a different degree of the key.

The total approved amount will be used to determine the degree by taking the modulus 7 of the value and adding 1 (the degree is an integer value from 1 to 7).

### 5. Debit to credit ratio

New notes are generated randomly based on the key, scale and chord, but they also tend to concentrate around the last played note. 

The strength of this tendency to concentrate around a note is determined by the ratio of debit to credit payment method. The larger this ratio (preference for debit), the larger will be the tendency of the note generation to stray further from the previous note. This can be heard as each of the instruments being able to navigate more freely through the full set of notes.
