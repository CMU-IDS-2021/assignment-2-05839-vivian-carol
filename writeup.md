# Exploring the musical landscape of David Bowie

![image](https://user-images.githubusercontent.com/24282522/111402007-65713100-8698-11eb-8884-1bedc7fe4038.png)

## Project Goals

In this project, we aim to visualize and explore the **trends and evolution of acoustic features in David Bowie's work from 1969 to 2018** (posthumous releases included).

We started with a large dataset (containing ~340,000 rows) that comprised of various features of albums and songs from the Billboard Top 200 through the decades. After exploring the data, we were mostly intrigued by the following features of each row in our data set: **the danceability, energy, tempo, and valence of each work**. This led us to the realization that with about half a century of data and a sizable list of features to analyze, what we most wanted to visualize was the evolution and musical tendencies of artists with incredible diversity in their work.

With that goal in mind, we chose David Bowie for his extensive and musically-divergent career. Bowie is well-known for his eccentric music styles and wide-reaching influence from his start in the 60s to his death in 2016.

This project consists of three parts:

- Charts allowing for visualization of acoustic features in the songs and the distributions of such features in various albums
- Comparison of the acoustic features in David Bowie albums vs. the overall features in other works by decade
An interactive music search feature that allows users to retrieve a list of recommended Bowie songs with selected acoustic features
- Ultimately, our analysis results aim to provide a different view of interpreting David Bowie's work. Moreover, besides searching for particular songs or albums in a traditional music search engine which often requires users to already have a song name in mind, how might we allow users find the work that better fits the context and mood they have in mind?

This project was completed by **Vivian Young** and **Carol Ho** for the Interactive Data Science (Spring 2021) course taught by Professors Adam Perer and Hendrik Strobelt.

## Design

A great design decision can help the audience navigate smoothly through large amounts of data. Our design decisions were made with an understanding of the existing mental model of how people understand music trends and with common music search behavior and expectations. The three main decisions are broken down as follows:

#### 1. Take advantage of familiarity and schemas surrounding music
It is commonly observed that in the US, people often discuss music preferences and trends within the context of the decade in which the music was produced. We can see an example of this in Wikipedia, where music trends are categorized by year: https://en.wikipedia.org/wiki/Music_history_of_the_United_States. Based on this observation, the x-axis of the scatter chart and the bar chart are order by the release date of the song or album. And furthermore, we included sliders for filtering the data in these charts and in the search feature to allow the user to fine-tune the albums and songs based on trends. Another feature we implemented is that the bar chart calculates the average acoustic feature data of albums produced in a decade to compare with a David Bowie album from that same time period in order to visualize similarities and differences in the musical trends of that decade.

#### 2. Utilize color and color psychology
Based on many findings from the world of social and cognitive psychology, it is known that we commonly have preconceived notions of color associations (an example being red signalling danger or yellow signalling caution). Though these schemas may differ by culture and personal experiences, generally, warmer colors, such as red, orange, yellow, are perceived as positive while cooler colors (e.g. blue, purple, green) are perceived as calmer or appear more unhappy. We observed that this understanding could be useful in visualizing **Valence**. 

> Valence: Describes the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).

Since this definition and term may be new to many in our audience, we aimed to familiarize users by connecting color schemas to the variable of valence. The color on scatter chart shows how the selected features, moods, and valence distribute across the albums, which shows the varied styles of Bowie's work. By clicking on the legend area to focus on a specific valence, the audience can also explore how an individual valence level distributes across albums.

#### 3. Iterate, iterate, iterate!
With many data visualization projects, ideas on paper may not translate to the eventual application on one's computer screen. When it came to some of our charts, we experienced many small hiccups when perfecting our visualizations and interactions.
Initially, we developed a bar chart by pairing the average album and the decade, with one album and one decade in one chart at a time. The comparison was explicit but was ineffective at communicating how these features (danceability, energy, and instrumentalness) developed through time. However, putting them in one chart created a massive amount of information; The chart became crowded with 64 bars of albums and the corresponding decade. And ultimately, it was difficult to discern the music trends from the decade bar lying between album bar. Therefore, we decided to overlay the bar and make the opacity to 50%, which allowed for a better comparizon visualization. We also explored how to label the overlay bar charts without distracting the audience. One idea was to place tooltips on each bar chart but it became impossible to trigger the tooltip when two bars are similarly tall. Our eventual solution was to mark the data of the decade bars with text, and the tooltip would only show when the user hovers over the album bar. 

## Development
### Development process
In the first week of this three-weeks-long project, we first independently gathered potential datasets that were of interest and then narrowed our options down to our top three dataset choices. With these three choices then decided, we discussed and wrote down a couple of compelling research questions for each dataset.


Then in the second week, we decided on utilizing the music dataset as the research questions were of most intrigue and worked on narrowing down our focus. The problem of working with too much all at once was definitely an issue we were actively trying to avoid so our next step was to narrow down our focus to highlighting an individual artist. Due to our mutual familiarity with David Bowie's eccentric and diverse body of work, we decided on visualizing his songs and albums throughout the years. After a brief discussion on potential visualizations and interactions, we then entered a period of independent work in order to create various charts and features separately. 


Our last week was spent iterating through multiple versions of the final result, fine-tuning interactions and minute details all throughout our application.

The following includes a general overview on how we both contributed during the application development process:

- **Scatter Chart - David Bowie's albums:** data query and charts built by Carol, interaction done by both of us
- **Bar Chart - David Bowie's albums with average features:** data query, interaction, and charts built by Carol
- **Acoustic feature song search:** data query, interaction, charts, and API implementation built by Vivian


### What aspect took the most time?
1. Cleaning / preparing the dataset
The type of columns in the dataset needed extra effort to tidy up. For example, we converted the date(varchar) to date(datetime) format to interact with the chart by year and we rounded up all the decimal numbers to make it easier to read. To get the music data by decade, we also spent time transferring the data value, group by and re-calculate the average and join the calculated results with SQL.

2. Chart customizations
Although the Altair and Streamlit API are straightforward and easy to implement/navigate, it took us some time to understand the limitations of customization. For example, the user can only interact with the whole line but not the line chart's data point. After digging into the documentation, we shifted our direction towards other charts. Thus, we spent quite some time iterating through various forms, colors, and interactions before settling on the choices present in the current application.

## Success Story

This project's goal was to explore various acoustic features of David Bowie's works and to provide a way for people to explore his music based on their preferences and mood. With the scatter chart distribution, we can tell that David Bowie's works are energetic but diverse in mood, instrumentalness, and danceability. This also suggests that his works are suitable for a diverse range of contexts. By comparing his work with those in the same decade, we can also tell that the energy and instrumentalness present in his work are distinct, both within that era and compared to the rest of his work. One discovery from the observing trends in the acoustic features is that associations between features can be difficult to predict and may be unexpected. When reading the definitions of the various features, we assumed that high energy levels might be correlated with high valence levels. But the scatter chart and the searching function suggested that were plenty of datapoints with low valence (sad) and simultaneously, low energy. Some questions we have regarding this realization are: How does Spotify calculate their data for songs? How do they use these features in their recommendations / search algorithms? And lastly, how are these features prioritized in the aforementioned algorithms? 


Nevertheless, we believe that this application will encourage users to think about musical features behind a song beyond the obvious and how they can be utilized in our daily streams.
