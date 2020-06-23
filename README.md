# The McGill Billboard Project

## Index
Most users will want to download the index to the dataset:

[billboard-2.0-index.csv](https://github.com/boomerr1/The-McGill-Billboard-Project/blob/master/billboard-2.0-index.csv)

The index is a CSV files with the following columns:

id, the index for the sample entry;
chart_date, the date of the chart for the entry;
target_rank, the desired rank on that chart;
actual_rank, the rank of the song actually annotated, which may be up to 2 ranks higher or lower than the target rank [1, 2];
title, the title of the song annotated;
artist, the name of the artist performing the song annotated;
peak_rank, the highest rank the song annotated ever achieved on the Billboard Hot 100; and
weeks_on_chart, the number of weeks the song annotated spent on the Billboard Hot 100 chart in total.
Sample entries for which we were unable to obtain audio or an annotation also appear in the index, but with the id, chart_date, and target_rank columns exclusively.
