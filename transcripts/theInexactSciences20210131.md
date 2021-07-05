# TIS Discord 1/31/21

_Tags: [[surrogation]], statistics, overfitting, [[compression]], transfer learning, machine learning._

[1:52 PM] suspended reason: Anyone know anything from math or statistics or set theory that can better express this intuition I've had?

[1:53 PM] suspended reason: I first realized it when characterizing genres in my high school music library

[1:53 PM] suspended reason: You can come up with a perfect taxonomy for a closed set—an ideal way of carving up a limited domain space

[1:54 PM] suspended reason: But as soon as new entries get in the mix, suddenly your categorization scheme isn't optimized to accomodate it, and distinctions that may not have mattered earlier (eg between grime and jungle, or electronica and techno, or whatever) do now matter

[1:54 PM] suspended reason: There's something about compression and information theory that makes this run, is my hunch

[1:55 PM] suspended reason: You're trying to "synopsize" the data, and that involves 1) making distinctions, 2) eliding distinctions

[1:55 PM] suspended reason: IIRC Shannon does talk about this, how any compression algorithm is optimized for a specific sub-set of language uses

[1:56 PM] suspended reason: If you do a Huffman encoding of the English alphabet, it's not gonna compress Spanish very well

[1:56 PM] suspended reason: or if you do it for one text that uses a lot of Xs and Ys, it'll perform terribly on standard English texts where Ts and Ss are most prominent

[1:56 PM] suspended reason: Crispy Chicken nicely sent me a book on information theory so maybe I need to read that... but there's so much these days

[2:01 PM] suspended reason: If this theory is true, apropos of the #[[surrogation]] talk, then the authors' concept of "robust alignment" is an impossibility

[2:01 PM] suspended reason: Robust alignment: when "mesa-optimizers with mesa-objectives... robustly agree with the base objective across distributions"

[2:02 PM] suspended reason: There :clap: is :clap: no :clap: accounting :clap: for :clap: unknown :clap: unknowns :clap: in an optimization scheme

[2:05 PM] suspended reason: problems emerge when we port one implementation to a new environment, where the previous implementation's choice elisions and distinctions no longer carve the new territory as they did in a previous environment (and this indexicality is inevitable)

[2:11 PM] ragged: This makes me think of clustering. You can separate your entries into groups, then each group can specify a distribution over entries. Assign a new entry to the group that gives it the max probability. If all groups give the new entry a low probability (below some chosen threshold), you might need a new group to account for this new “type”. But a type with one member isn’t very helpful; you might have to re-do your whole taxonomy/clusters to account for this anomaly

[2:18 PM] suspended reason: Hmmm yeah

[2:19 PM] ragged: “transfer learning” in ML seems relevant here

[2:19 PM] suspended reason: Especially if you were optimizing like, there are blue eggs and red cubes, and the blue eggs are "good" (you keep them) and the red cubes are "bad" (you discard)

[2:19 PM] suspended reason: Let's say that, in reality, we know that what "matters" is picking eggs, because cubes are useless

[2:20 PM] suspended reason: But you could imagine that, if a categorization model was trained on blue eggs and red cubes, and then got shown red eggs and blue cubes, it might end up selecting for all the blue cubes!

[2:21 PM] suspended reason: There are distinctions (blue cubes bad too, red eggs good too) that you have no need to specify in the training environment because they're irrelevant

[2:21 PM] suspended reason: But in a new environment they're suddenly the relevant thing

[2:22 PM] suspended reason: And I suspect that, for a given training set, there will always be a hypothetical environment that its previous schema of distinctions and elisions will "fail" to represent in the new environment

[2:22 PM] suspended reason: Maybe this is a wrong hunch

[2:22 PM] suspended reason: But it also reminds me of the words problem: there are a ton of hypothetical objects that exist "between" existing carved spaces/words

[2:23 PM] suspended reason: If we invent something that's both a stool and a table well what do you call it, suddenly the distinction that made sense between a stool and a table falls apart, the words are optimized (indexical) to one environment, and a new environment means they suddenly no longer "fit"

[2:35 PM] suspended reason: Oh man

[2:35 PM] suspended reason: birth control is a perfect example of this

[2:35 PM] suspended reason: Evolution controlled for so many changing environments with its coupling of sex and reproduction

[2:35 PM] suspended reason: But it never could've foreseen birth control

[2:35 PM] suspended reason: so making sure that pleasure requires active insemination of the egg was totally unnecessary

[2:36 PM] suspended reason: You just needed to make sure the sperm got inside the vagina

[2:36 PM] suspended reason: But birth control changes the game, a new unforeseen technological advance means that a previous assumptive coupling has broken down

[2:37 PM] suspended reason: lol or previous foul rules in the NBA assumed any NBA player had a high enough free-throw % that fouling was, on net, bad for the opposing team (because the free throw meant they'd always score at least 1 point, on average, with a 50%+ free-throws made rate)

[2:38 PM] suspended reason: and then Shaq joins the league with like a 20% from the line and suddenly Hack a Shaq exists

[2:38 PM] suspended reason: and it's strategically better to just foul constantly than to actually play the game normally

[2:38 PM] suspended reason: the game "degenerates" under a new "hack" that is enabled by a changing environment (new data)

[2:51 PM] ragged: I was gunna say this seems especially true of language which changes over time and has local nuances, but most environments and datasets in the wild are like that lol

[2:51 PM] suspended reason: right?

[2:51 PM] suspended reason: I have to imagine the best you can do is optimize over a projected future

[2:52 PM] suspended reason: but you can't optimize the unknown unknowns that are the future perfectly

[2:52 PM] suspended reason: new environmental factors and confounders and decouplings will inevitably emerge at some point

[2:52 PM] suspended reason: maintenance of alignment, then, becomes more important that "getting it right the first time" (at least in an AI context)

[2:56 PM] ragged: And curate your training set to be as close to reality’s generative model as it currently stands

[2:56 PM] ragged: Thus the approach to train AI systems on the whole damn internet

[9:06 PM] snav: i think compression is another good approach to the problem you pose, assuming the question can be posed as "how do you most efficiently categorize a set of elements such that you can find or represent one element among the entire set as efficiently as possible?"

[9:06 PM] snav: in particular we can look at "compression ratio" https://en.wikipedia.org/wiki/Data_compression_ratio
Data compression ratio
Data compression ratio, also known as compression power, is a measurement of the relative reduction in size of data representation produced by a data compression algorithm. It is typically expressed as the division of uncompressed size by compressed size.

[9:06 PM] snav: so basically the point of a compression algorithm is to reduce the size of the input data to a smaller size of output data

[9:07 PM] snav: creating good divisions allows for a more "dense" encoding -- specifically you can encode n points of data in log(n) size if you have a "perfect" compression algorithm, where every element has an exact "slot" in the tree created by divisions

[9:08 PM] snav: so the "naive" algorithm here is encoding data points along a fixed binary tree structure

[9:11 PM] snav: so lets say you have 8 songs and you have 3 genres, and each of the songs can be precisely identified by their combination of the 3 genres. so you'd make a tree that looks like
             A
       Y/         \N
       B           B
    Y/   \N     Y/   \N
    C     C     C     C
  Y/ \N Y/ \N Y/ \N Y/ \N
  1   2 3   4 5   6 7   8

[9:12 PM] snav: so then you could encode e.g. song 6 as ~A + B + ~C

[9:12 PM] snav: aka in 3 bits: 010

[9:12 PM] snav: however let's say suddenly you get a lot of other songs with an exact genre combination as 6:

[9:13 PM] snav:
             A
       Y/         \N
       B           B
    Y/   \N     Y/   \N
    C     C     C     C
  Y/ \N Y/ \N Y/ \N Y/ \N
  1   2 3   4 5   6 7   8
                 D|
                  9
                 E|
                  10

[9:14 PM] snav: now in order to encode song 6 vs song 9 or 10, you need 2 extra bits of data:
6 = ~A + B + ~C + ~D + ~E
9 = ~A + B + ~C + D + ~E
10 = ~A + B + ~C + D + E

[9:14 PM] snav: in other words, the number of bits you need to encode the entire set of data is the maximum depth of the tree

[9:15 PM] snav: so there's this idea of having an optimal compression, which is an arrangement of divisions that creates a tree of minimum depth, thus allowing all elements to be represented with the fewest bits possible

[9:15 PM] snav: there's a bunch of really cool algorithms that attempt to solve this, by adjusting the tree's shape as new elements are added

[9:16 PM] snav: a notable one is the treap: https://en.wikipedia.org/wiki/Treap (which uses a trick of "randomness" to achieve optimality) plus other forms of "self-balancing" trees https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree (like the red-black tree, commonly used in databases and file systems https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)

[9:18 PM] snav: for certain applications such as language, you have specialized data structures like the "huffman tree", which do quite well https://en.wikipedia.org/wiki/Huffman_coding -- they work by encoding prefixes rather than just dichotomies

[9:19 PM] snav: sorry for dorking out about this lol

[9:19 PM] snav: i just think it's a cool topic

[10:57 PM] suspended reason: No this is great! This kinda thing is exactly what I hoped people would mention. I remember the vague outlines of this stuff from an information theory class I took in college but only that

[2:36 PM] suspended reason: Yeah, I think that's exactly the concept handle I needed for search

[2:36 PM] suspended reason: What I've been working on mentally is this idea that's halfway between compression and transfer learning

[2:37 PM] suspended reason: or rather, a pattern between them, it's probably been coined somewhere at a more abstract level of math/theory

[2:37 PM] suspended reason: That is, my understanding of compression is it uses observed regularities in a dataset as the basis of its compression

[2:38 PM] suspended reason: These patterns allow it to use shorthand: if "qu" always gets used together in English, then it's more efficient to assign "qu" to a shorter # of bits and "q" on its own to a longer # of bits

[2:39 PM] suspended reason: Especially in lossy compression, there's this logic of eliding certain distinctions and conflating certain differences as "close enough" pragmatically

[2:40 PM] suspended reason: The only metaphor or term I have to think about this is "fit" (in the evolutionary sense): there is a fit between a compression schema and a data set

[2:41 PM] suspended reason: If a compression schema treats any instance of "qu" or "q!u" (e.g. "qi") as interchangeable, then you'll get like 99+% transmission accuracy in English, high fitness, only slightly lossy

[2:42 PM] suspended reason: If you apply this conflation to Spanish texts, you're still doing OK

[2:42 PM] suspended reason: but if you apply it to a transliteration of Mandarin or something, you're probably fucked—I don't know much about the language, but I feel like I've seen a lot of "qi" action, @crispy_chicken can confirm

[2:42 PM] suspended reason: There's low fitness between the schema and the dataset

[2:45 PM] suspended reason: In ML transfer learning situations—and I understand this very crudely, so someone please correct my misuse of terms or conceptual errors or whatever—it seems like if you had an autoencoder train on a bunch of objects, and in the training set, tables were always wooden and chairs were always metal, if you were to show that autoencoder metal tables and wooden chairs, it may well identify them all incorrectly because it uses material only to represent the entire identity of the object

[2:45 PM] suspended reason: There is a metonymic [[surrogation|surrogate]] in place; the algorithm, in its training set, could reliably guess an object's identity merely by identifying its material (a single property of the whole)

[2:46 PM] suspended reason: But when this assumption of co-occurrence is no longer true of a dataset, you're fucked.

[2:46 PM] suspended reason: Now, if I'm thinking about the letter of rules as a compression (or "specification") of spirit, we hit the same issue, right?

[2:47 PM] suspended reason: I'm a lawmaker and I make a law whose spirit is preventing underage kids from getting high off amphetamines

[2:47 PM] suspended reason: So I get the DEA together and we look at all the street drugs getting sold as "speed," and realize they all share some common molecular or structural pattern

[2:48 PM] suspended reason: So we say, alright, let's ban the use of that pattern

[2:48 PM] suspended reason: Because the structural pattern and the amphetamine effects, in our current environment, reliably co-occur, we can just ban one in order to convey the spirit

[2:49 PM] suspended reason: But, if someone comes in and changes the "environment" by inventing drugs that differ from the structure, while achieving the same effects, suddenly this [[surrogation|surrogate]] has broken down, because a previous regularity in the dataset no longer holds in our new world

[2:50 PM] suspended reason: Now, without knowing the math, it seems possible to me that there is no possible specification, or no possible [[surrogation|surrogate]], that can robustly achieve the spiritual [[intent]] across all possible hypothetical worlds

[2:51 PM] suspended reason: You might be able to "go upstream" somehow and ban all chemicals that release a certain amount of dopamine or whatever, and in this way, you truly do end all possibility of dopaminergic recreational drug-use (because you've effectively banned the thing itself you're worried about, rather than banning a [[surrogation|proxy]] that reliably co-occurs in the current environment)

[2:51 PM] suspended reason: But as long as you use [[surrogation|surrogates]] good chance you're fucked

[2:52 PM] suspended reason: Anyway, if this is true or there's mathematical grounding/a proof for it, it seems to have major implications for the AI alignment conversation

[2:52 PM] suspended reason: Because AI alignment can only be thought of as something to maintain & evolve, rather than as something to design and let run

[2:53 PM] suspended reason: As time goes on, the "fitness" between the AI and the environment will slowly degenerate—naturally, because shit changes on its own, but also anthropogenically, because humans purposefully game static implementations of spirit in letter

[3:14 PM] suspended reason: Taking the transfer learning problem and making it generic to some context transfer problem: When a system of knowledge, evaluation, or perception is ported from one context, where it has been successful, to a new context, in which it is untested, that system's real patterns of parsing and handling within the new context may radically differ from the anticipations of its designers.

[3:15 PM] suspended reason: hmmm maybe transfer learning, at least as framed on Wikipedia, isn't exactly what I want, because when you transfer a neural network from e.g. identifying cars to identifying trucks, you know you're moving it to a new context where it's likely to not perform well

[3:16 PM] suspended reason: whereas this is a problem of the real world dataset differing from the training set

[3:16 PM] suspended reason: the difference in performance expectations vs behavior is glass half empty vs glass half full

[3:17 PM] suspended reason: In both cases, a domain shift or distributional shift

[3:19 PM] suspended reason: But from the eyes of human beings controlling the algorithms, meaningfully different scenarios when you apply a car id nn to truck id'ing, vs when you apply a car id nn to real-world cars ("test set"?) and find out that your training data wasn't perfectly representative and now the nn thinks every red stationwagon is a ford

[3:20 PM] suspended reason: ohhh shit this is "overfitting," right?

[3:22 PM] suspended reason: except I don't love this definition:
The essence of overfitting is to have unknowingly extracted some of the residual variation (i.e. the noise) as if that variation represented underlying model structure.[3]:45 In other words, the model remembers a huge number of examples instead of learning to notice features.
Who is to determine what is noise vs signal without a conceptual frame or causal interpretation? Like, is there any way to ground what is noise vs signal in a dataset, other than by appealing to some other (perhaps larger) dataset?

[3:23 PM] suspended reason: Is "oh shit, I thought all tables were made out of wood but really it's just the tables in my dataset that are made out of wood" overfitting? Because it seems like it. But framing the table/wood conflation as "noise" seems off

[3:27 PM] suspended reason:
Overfitted models … are often free of bias in the parameter estimators, but have estimated (and actual) sampling variances that are needlessly large (the precision of the estimators is poor, relative to what could have been accomplished with a more parsimonious model). False treatment effects tend to be identified, and false variables are included with overfitted models. … A best approximating model is achieved by properly balancing the errors of underfitting and overfitting.

[3:27 PM] suspended reason: I love this. "How long do you cook pasta?" "A best approximating model is achieved by properly balancing the errors of undercooking and overcooking"

[3:32 PM] suspended reason: Ah, I see why "noise" makes sense—the idea is that your sample should be random in the first place, so any variations compared to non-sampled members of the same set is fairly described as "noise." In real life though, data sets aren't gonna be perfectly randomly sampled tho, and there's nothing "random" or "noisy" about the features specific to the present-moment environment, e.g. "all cars are metal" (we could imagine future cars not being metal, and this again fucking up id)

[3:32 PM] suspended reason: Gah I always do this, I write too many thoughts and no one is gonna end up reading this, but I'm also completely statistically and mathematically illiterate so I can't think through this stuff on my own