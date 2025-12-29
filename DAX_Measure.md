# Key Analytics Measure

### The Loyalty Score (Artist Affinity)
This measure calculates the average time spent per song for each artist. A higher score indicates "loyalty," meaning I listen to their tracks for longer durations rather than skipping.

**DAX Formula:**
```dax
Loyalty Score = 
DIVIDE(
    SUM('dim_artist_stats'[total_listening_time_mins]), 
    SUM('dim_artist_stats'[song_count]), 
    0
)
```

### Why this matters
Volume vs. Quality: A simple "Song Count" only shows how many tracks are in a playlist.
Listener Behavior: By dividing total time by song count, we identify artists whose songs are played through to the end, identifying true "top-tier" favorites.
Threshold: In this project, a score of 3.64 represents the global benchmark for a "loyal" track.

### Business Impact
Insight: This metric identifies "High Affinity" artists regardless of their total track count.
**Result**: In this analysis, **Ariana Grande** achieved a **loyalty score of 3.54**, while the **global average was 3.64** minutes per track.
