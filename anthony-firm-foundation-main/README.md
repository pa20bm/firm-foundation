# anthony-firm-foundation

Playing around with annual volumes of the Firm Foundation religious journal.

## About this project

The *Firm Foundation* was a weekly religious journal begun in the 1880s serving members of the Stone-Campbell religious movement eventually known generally as the Churches of Christ. Because Churches of Christ have no formal denominational structure to adjudicate disagreements or define the limits of the group's doctrine and practice, journals such as *FF* in the mid to late 20th century served as informal, but no less powerful, arbiters of what made a preacher, college, or worshpper a "true" member of the group. The "editor bishops" who ran these journals became gatekeepers of correct doctrine and practice, and the journals themselves are among the best ways to assess the views and assumptions of mainstream Churches of Christ, as well as what issues sparked concern or even alarm among the movement's leaders.

## Goal

For this project, I will select four issues from the forty annual volumes (one per decade), clean the text, and see what there is to analyze.

## Progress

**Jan. 27**: Uploaded raw plain-text files of the annual volumes.

**Feb. 1**: Used random number generator to select issues from each of the four decades, then worked on the issue from Aug. 10. 1976, by:
1. Removing line breaks within paragraphs by replacing new lines without preceding periods with spaces.
2. Removing line breaks following commas.
3. Removing double spaces.
4. Replacing the OCR error space-dot-space with just dot-space.
5. Working to identify other consistent OCR errors or display type whose removal could be routinized (not finding a whole lot).
6. Removing line breaks after abbreviations for books of the Bible that the text treats as ends of sentences.

**Feb. 3**: Repeated steps 1-6 for remaining three issues by using "Find in Files."

**Feb. 8**: Pulled out tables from two issues: May 22, 1945, which I had already cleaned, and Jan. 4, 1976, which I extracted specifically for this purpose. The table from 1945 ended up with stretches where columns were split into separate lines and needed to be fixed by hand. Not sure if there's a way to do that automatically. The 1976 table was much cleaner, although it did require hand-inputting one line of data that OCR had garbled beyond recognition. Played with the 1945 table in Open Refine.

**Feb. 9**: Hung up on trying to find a RegEx that will allow me to find all-caps phrases _and_ add "@@" without replacing the whole string. There are too many all-caps phrases (datelines, for example) that I don't need to flag, and I can't seem to figure out a way to find them without replacing at least the first word with the symbols.

**Feb. 15-16**: Uploaded 1/4/1976 table on Church of Christ presence by state (as measured by number of cities with at least one congregation) to Tableau, and created a map shading each state by percentage. I had fun with colors to see if it resembled the election maps with which we're so familiar, [and it seems to](https://public.tableau.com/profile/paul.anthony3275#!/vizhome/1976ChurchesofChristbyState/Sheet1?publish=yes). Curious about the relationship between this density and today's political landscape, I uploaded a data with the 2020 Democratic presidential vote share and played with ways of visualizing it compared to the CoC data. First, Tableau [clustered the states](https://public.tableau.com/profile/paul.anthony3275#!/vizhome/ChurchesofChristxPresidentialResultsClusters/Sheet1?publish=yes) into three groups that more or less translate to "high CoC/low Dem states," "low CoC/high Dem states," and "muddling through" states, although I'm not sure exactly how it determined which states are in which cluster. Finally, I put the two tables into a scatterplot, which showed [an R2 slope of -0.22](https://public.tableau.com/profile/paul.anthony3275#!/vizhome/ChurchesofChristxPresidentialResults/Sheet1?publish=yes), which *seems* correlative, although obviously not causative. I couldn't figure out how to make the scatterplot label states instead of percentages.

**Feb. 22-23**: Well, now I see why Tableau is so popular! It was *much* easier to create a scatterplot there than with R Studio/GG PLot. Nevertheless, I successfully worked through Healy's tutorial, then successfully – with some help from Ellie – created my own scatterplot mapping a rough measure of Church of Christ density against Democratic support in the 2020 presidential election.

**March 9**: For my topic modeling, I chose 12 editorials from the 1960 volume of the  Firm Foundation ending on Nov. 1, the last issue published before the presidential election. I struggled to find a background reference material. Archives of the Christian Century, America, Catholic Reporter and Billy Graham’s sermons are all either unavailable or can’t be copied into plain text documents for analysis. So in the end, I just grabbed 12 editorials from another Church of Christ journal I have, the Gospel Advocate. They redesigned in the middle of the year, and the pre-redesign text is much harder to parse, so I took 12 editorials, the first few of which overlap with the dates of the Firm Foundation  editorials.

I ran both through Topic Modeling and came up with 10 groups of topics that were slightly different, although interpreting them remains something that isn’t quite clear to me.

For the FF, topics included groups centered on missionary activity (“gospel,” “community,” “northeast,” “tent making”), the presidential election featuring eventual winner John F. Kennedy and his Catholicism (“political,” “religion,” “Catholic,” “candidate”), movement-specific issues and controversies (“brethren,” “idols,” “debaters”), the alleged decline of society (“end times,” “world,” “troubled”), and calls for new subscriptions (“special,” “issue,” “subscription,” “year”).

In GA, the topic were obviously similar, although with a topic devoted to the movement’s distinctive a cappella emphasis (“music,” “singing,” “songbooks,” “instruments”) and three topics that all revolve around the dire state of society, either the threat from Catholicism personified in JFK, or “evil” and “apostasy.”

When I combined them into 20 documents and ran them through the topic modeler, it actually became less coherent, rather than more, and I’m not sure what that means.

**March 15**: I tooled around with the Wikidata Query Service, looking through Churches of Christ-related search terms, and was surprised to find only three "instances of" a magazine with the "main subject" of Churches of Christ. I then searched for the *Christian Chronicle*, a movement-affiliated newspaper with more of a journalistic (rather than polemic) inclination. Of course, I realized later that since it's a newspaper, and not a magazine, it shouldn't have shown up in the list anyway, but never mind. Although correctly listed in Wikipedia as affiliated with Churches of Christ, the Wikidata did not include its affiliation, so following the lead of the data entries for *Firm Foundation* and the *Gospel Advocate*, I added a "main subject" of Churches of Christ for the *christian Chronicle*.