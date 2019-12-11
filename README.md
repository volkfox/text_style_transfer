# Text Style Transfer in Fiction

This is a companion repo to paper 'Literary Style Transfer with Sequence Models and Rejection-Pass Filtering' that helps with experimenting with style in literature.

The main idea in this project is a brute force rejection-pass architecture that parses the content source for lexemes and uses a text generator (GPT-2) fine-tuned for the target style to generate many samples. If there are samples matching a given content lexeme in embedding, it is being replaced. Since replacement lexemes come from a distribution of style author, this achieves a style shift in the output text.

Here is an example from Ayn Rand transformed in Jane Austen style:

```
She sat at the window of the train, her head thrown back, one leg stretched across
to the empty seat before her. The window frame trembled with the speed of the
motion, the pane hung over empty darkness, and dots of light slashed across the
glass as luminous streaks, once in a while.

Her leg, sculptured by the tight sheen of the stocking, its long line running
straight, over an arched instep, to the tip of a foot in a high-heeled pump, had a
feminine elegance that seemed out of place in the dusty train car and oddly
incongruous with the rest of her. She wore a battered camel's hair coat that had
been expensive, wrapped shapelessly about her slender, nervous body.  The coat
collar was raised to the slanting brim of her hat. A sweep of brown hair fell back,
almost touching the line of her shoulders. Her face was made of angular planes, the
shape of her mouth clear-cut, a sensual mouth held closed with inflexible
precision. She kept her hands in the coat pockets, her posture taut, as if she
resented immobility, and unfeminine, as if she were unconscious of her own body and
that it was a woman's body. She sat listening to the music. It was a symphony of
triumph. The notes flowed up, they spoke of rising and they were the rising itself,
they were the essence and the form of upward motion, they seemed to embody every
human act and thought that had ascent as its motive. It was a sunburst of sound,
breaking out of hiding and spreading open. It had the freedom of release and the
tension of purpose. It swept space clean, and left nothing but the joy of an
unobstructed effort. Only a faint echo within the sounds spoke of that from which
the music had escaped, but spoke in laughing astonishment at the discovery that
there was no ugliness or pain, and there never had had to be. It was the song of an
immense deliverance.
```
Original content likelihood w.r.t. Austen: 0.00651407

Machine Generated: Jane Austen style transfer:

```
She sat at the window of the train for half a minute, and as she looked up, she stretched 
one leg across to theempty seat in front of her. The window frame trembled with the speed 
of the motion, the unnerveness of thetable amidst the scattered glasses, and the 
distressing tones of the glass pressed against the glass as luminousstreaks obtruded the view.
Her leg, sculptured by the tight sheen of the stocking, its long line running straight, from 
the ankle to the fore-foot, to the tip of a foot in a glide, had a feminine elegance that 
seemed out of placein the dusty train car and oddly incongruous with the rest of her. She 
was a scantily shaven woman: her hairwas very short but expensively cut, her face was a little
hoary and attached to a rather pensive, nervous body.The coat collar was raised to the slanting
yellow humbug of her hat. A sweep of brown hair fell back, affordinga quick view of her face. 
Her hair was striking, as if unsubdued by ill-timed gravity, and almost turned into aveil 
against her face, her sensual mouth held closed with inflexible precision. She put one hand 
tied behind herface, and her heart leaped against the stomach with sudden feeling, as the cottony, 
trembling hand was about toembrace body her woman’s body. She was in a reverie, as he entered 
the room. It was a symphony of triumph.The Tilneys were at the instrument; they determined, 
boldly among themselves they were the rising stars, theywere the lights of the chambers, where 
the utmost importance was the form of upward motion, the perfectionthey encumbered, to examine 
and express themselves in all their grandeur as if they had been conscious of it.It was a sunburst 
of sound, breaking out of hiding and spreading over the whole room. It had the freedom ofrelease 
and the tension of purpose. It swept space clean. There was a feeling from which the music 
had escaped, and spoke in laughing astonishment at the discovery that there was no ugliness or pain, 
and there never had hadto be. It was the sound of a great pianoforte
```
Transformed content likelihood delta towards Austen + 0.03932239


Architecture:

![Rejection-Pass architecture](/images/RPF.png)

Here we provide the code for RPF generator and style classifier with NER (name entity removal).
RPF generally needs a V100 or better GPU, but sometimes can work on a free Google collab tier.

Enjoy!


