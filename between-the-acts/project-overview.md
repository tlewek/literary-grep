# The Fragments of Virginia Woolf’s *Between the Acts*

## Data

This project attempts to identify, quantify, and visualize the fragments found in Virginia Woolf’s final novel, *Between the Acts*, published in 1941. In this context, fragments indicate the instances of text bounded by ellipses on either side—e.g. “. . . flying mounting through the air . . .” (15). Such instances speak to the wide array of voices, both dialogic and narrative, throughout the novel. Yet they also seem too numerous and, therefore, too difficult to serve as the basis for an interpretation through close reading alone. Where do these fragments occur in the novel? Who utters them? In which spaces are they uttered? Answering these questions, by compiling and visualizing a dataset, might open new avenues of insight.

## Visualizations

links tk

## Processes

To identify the fragments, I downloaded a [plain text version](http://gutenberg.net.au/ebooks03/0301171.txt) of the novel, ran a `grep` search using regular expressions, and performed some additional cleanup. Next, I created a [`.json`](http://www.json.org/) file where each fragment became an object. Within each object, I added `text`, `speaker`, `setting`, and `page` strings. The actual text of the fragment became the value of the `text` string, the name of the character who utters the fragment became the value of `speaker` string, the setting in which the fragment is uttered became the value of `setting` string, and the `page` values refer to page numbers from the 1941 Harcourt edition. Adding the `speaker`, `setting`, and `page` values involved a non-programmatic, human reading of the novel.

With the `.json` file complete, I converted it to an Excel spreadsheet and loaded the data into [Tableau Public](https://public.tableau.com/s/) where I produced the following visualizations mentioned above.

## Challenges

This data collection and creation was not without challenges. For example, my `grep` search for any character, multiple times between ellipses (I used the regular expression `. . .(.*). . .`) returned data that required cleanup. In fact, this search often returned results such as

> . . . And Lord! The jangle and the din! The very cows joined in. Walloping, tail lashing, the reticence of nature was undone, and the barriers which should divide Man the Master from the Brute were dissolved. Then the dogs joined in. Excited by the uproar, scurrying and worrying, here they came! Look at them! And the hound, the Afghan hound . . . (184)

Should text like this example, which spans eight sentences, count as a fragment? I decided that it should not and, subsequently, refined my definition of a “fragment” to text at the sentence or sub-sentence level. Therefore, I did not include strings that spanned multiple sentences in my `.json` file. A string could end with a period, question mark, or exclamation before the closing ellipses, but such punctuation could not exist in the middle of that string.

### Speaker

Often there is no distinct speaker uttering the fragment (in the case of the audience), or the fragment comes from a collection of speakers (in the case of the chorus).

Characters are also actors in the play. In these cases, I’ve given their real names first, followed by the characters they portray in the play in parentheses.

The several fragments attributed to Mrs. Lynn Jones are more ambiguous than presented here. Woolf ostensibly places this character in conversation with Mrs. Etty Springett—Lynne and Etty are widows, who share a house, attending the play together—but it seems that former merely talks at the latter.

“Someone,” “audience,” “villagers,” “two cronies” are indistinct but accurate values.

### Setting

Woolf often highlights the setting of an uttered fragment by providing details in the text adjacent to the fragment itself (e.g. “between the trees,” “among the bushes”). More often, however, she does not, and I’ve had to rely on a small, controlled vocabulary (e.g.  “outdoor theater (stage)” or “outdoor theater (seats)”) to generate this data.

## Works Cited

Woolf, Virginia. *Between the Acts*. Harcourt, 1941.