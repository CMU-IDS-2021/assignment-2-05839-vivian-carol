# Exploring the musical landscape of David Bowie

![A screenshot of your application. Could be a GIF.](screenshot.png)

TODO: Update screenshot

TODO: Short abstract describing the main goals and how you achieved them.

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

A great design decision can help the audience navigate smoothly through large amounts of data. Our design decisions were made with an understanding of the existing mental model of how people understand music trends and with common music search behavior and expectations. The three main decisions are as follows:

#### 1. People relate musical styles with certain decades
It is commonly observed that in the US, people often dicuss music preferences and trends within the context of the decade in which the music was produced. We can see an example of this in Wikipedia, where music trends are categorized by year: https://en.wikipedia.org/wiki/Music_history_of_the_United_States. Based on this observation, the x-axis of the scatter chart and the bar chart are order by the release date of the song or album. And furthermore, we included sliders for filtering the data in these charts and in the search feature to allow the user to fine-tune the albums and songs based on trends. Another feature we implemented is that the bar chart calculates the average acoustic feature data of albums produced in a decade to compare with a David Bowie album from that same time period in order to visualize similarities and differences in the musical trends of that decade.

#### 2. The psychology effect of color
Based on psychology study, color evoke emotions connection. Though it might different by culture and personal experience, but generally, warm colors, such as red, orange, yellow are perceive as positive, while bool colors such as blue, purple and green are perceive as calm, sad and indifference. This emotional connection suit well with the definition of **Valence**. 

> Valence: Describes the musical positiveness conveyed by a track. Tracks with high valence sound more positive (e.g. happy, cheerful, euphoric), while tracks with low valence sound more negative (e.g. sad, depressed, angry).

Since the definition of valence is new for most of the audience, connecting the meaning of color and the variable at valence help reduce cognitive load. The color on scatter chart shows how the selected features, moods and valence distribute across the albums, which shows the variety style of Bowie's work. By clicking on the legend area to focus on a specific valence, the audience can also explore the how individual mood distribute across albums.

#### 3. Bar chart comparison development
Initially, we develop a bar chart by pairing the average album and the decade, with one album and one decade in one chart at a time. The comparison explicit, but it tells nothing about how these features(the danceability, energy, and instrumentalness) develop through times. However, putting them in one chart creates a massive amount of information: the chart is crowded with 64 bars of albums and corresponding decade. And it's hard to tell the music trend with the decade bar lying between album bar. Therefore, we decided to overlay the bar and make the opacity to 50%, which allows the audience to tell the overlay and exceed area by color. We also explore how to label the overlay bar charts without distracting the audience; we placed tooltips on each bar chart, but it's impossible to trigger the tooltip when two bars are similarly tall. We improved by marking the data of the decade bars with text, and the tooltip shows only when the audience hovers on the album bar. 

TODO: **A rationale for your design decisions.** How did you choose your particular visual encodings and interaction techniques? What alternatives did you consider and how did you arrive at your ultimate choices?

## Development
### development process
In the first week of this three-weeks-long project, we first independently gathered potential datasets that were of interest and then narrowed our options down to our top three dataset choices. With these three choices then decided, we discussed and wrote down a couple of compelling research questions for each dataset.
Then in the second week, we decided on utilizing the music dataset as the research questions were of most intrigue and worked on narrowing down our focus. The problem of working with too much all at once was definitely an issue we were actively trying to avoid so our next step was to narrow down our focus to highlighting an individual artist. Due to our mutual familiarity with David Bowie's eccentric and diverse body of work, we decided on visualizing his songs and albums throughout the years. After a brief discussion on potential visualizations and interactions, we then entered a period of independent work in order to create various charts and features separately. Our last week was spent iterating through multiple versions of the final result, fine-tuning interactions and minute details all throughout our application.

The following includes a general overview on how we both contributed during the application development process:

- **Scatter Chart - David Bowie's albums:** data query and charts built by Carol, interaction done by both of us
- **Bar Chart - David Bowie's albums with average features:** data query, interaction, and charts built by Carol
- **Acoustic feature song search:** data query, interaction, charts, and API implementation built by Vivian


### What aspect took the most time?
1. Prepare the data for the charts
The type of columns in the dataset need extra effort to tidy up. For example, we convert the date(varchar) to date(datetime) format to interact with the chart by year and rounding up all the decimal numbers to make it easier to read. To get the music data by decade, we also spent time transferring the data value, group by and re-calculate the average and join the calculated results with SQL.
2. Customize the color and interaction of the charts
Altair and Streamlit API are straightforward and easy to implement. But it took us some time to understand the limitation of customization. For example, the user can only interact with the whole line but not the line chart's data point. After digging into the gallery and documentation, we shift our direction to other charts. Therefore, we spent some time iterated various forms, colors, and interactions before coming up with the current application.

## Success Story(WIP)

TODO:  **A success story of your project.** Describe an insight or discovery you gain with your application that relates to the goals of your project.