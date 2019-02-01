# Guide to the Interactive Web Demo
This is a guide to the Interactive Web Demo of the Story Generation System, which can be found here: [cwc-story.isi.edu/](http://cwc-story.isi.edu:5002)

There are two modes to the Interactive Demo `Auto` (the first page when you go to the link), 
and `Interactive` (reached via the top nav bar). This document details how to interact with the system. Details of it's configuration and backend are in the [README], (https://github.com/isi-vista/Plan-and-write#web-demo), which you can only access if you have perms to that repo.

## Auto Mode

Enter a story title or topic into the textbox, and the system will generate:
* a storyline
* a story _directly_ from the title (without using the storyline) (`Title to Story`)
* a story using the storyline to guide the generation (`Plan and Write`)
* a story using both the storyline and some additional models that bias the system toward certain qualities (such as creativity or relevance) (`Plan and Learn to Write`)

That's it! Now you can compare how the outputs differ and see what you think.


## Interactive Mode

As before, enter a title or topic into the textbox, and click `Start`. This begins a collaborative session between you and the chosen model.

Now at any step you can write your own storyline words, or click `Suggest the Next Phrase` to have the model generate it.
Once all Storyline words are filled in, you can write your own story sentences, or click `Suggest the Next Sentence` to have the model write it.

If you want the model to generate all storylines at once (so you can jump to working on the story) you can click `Suggest the Next Sentence` in the Story section, _directly_ after `Start`, and it will fill in all the storyline phrases.
If you want it to generate everything at once (including the story) before you edit it, you can click `Generate Story` after `Start`.

You can delete and re-write anything that either you or the model have entered, whether at the middle, beginning, or end. You can get the model to regenerate those portions too.

Clicking `Clear` on either the storyline or the story section will clear all the text entered in the respective section.


## Advanced Options (Dials to fiddle with)
Definitely play with these options to tune the output!
* _Diversity_ numbers (followed in the UI by the appropriate ranges) correspond to softmax temperatures.
This is a measure of "unusualness" and controls how conservative the model is in its choices. Lower numbers
mean it will only generate words that it considers very likely, higher numbers will make it explore more - which may make it more 
creative, but may also make it less coherent.
* _Dedup_ prevents the system from re-using a word that it has already used (it enforces uniqueness of generated words).
It only affects storylines.
* _Maxlen_ cuts the model off at an integer maximum amount of words. The model also will stop generating when it thinks it is done, but this can be used to 
make the generations much shorter than the training data.
* _Use gold storylines_ this causes the system to try to find a gold-standard storyline that will match the title you entered, 
instead of generating one. If it can't find one it will generate one anyway. Gold standard storylines are generally more lexically diverse than generated storylines,
but mostly this is useful to ensure a fixed title -> storyline relationship (since generated storylines are not cached, so they will change every time you regenerate.)
* _Rapid debugging mode_ allows you to re-click `Generate` before the model is finished with its last generation. This causes some confusing UI behavior, but is beneficial for debugging sometimes.

## Things to Note

There is some element of randomness, so storylines and stories (or portions of them) may re-occur across different generations, but are not guaranteed to. This is more likely
at lower `diversity` values.  For instance, at low `diversity` values, if you regenerate just the final sentence of a story multiple times, it is likely to stay the same (as it is conditioned on the same thing and the model is conservative). At high `diversity` values even the final sentence is likely to change.
