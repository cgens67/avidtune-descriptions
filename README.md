# AvidTune Descriptions Repository

Community-driven editorial reviews, background lore, and descriptions for albums, singles, EPs, and artists in [AvidTune](https://github.com/cgens67/AvidTune).

---

## Directory Structure

```text
avidtune-descriptions/
├── albums/
│   ├── artists/
│   │   ├── {artist_slug}/
│   │   │   ├── {playlistId}.txt
│   │   │   ├── {album_title_slug}.txt
│   │   │   └── {albumId}.txt
│   │   └── ...
│   ├── {playlistId}.txt
│   └── {album_title_slug}.txt
│
└── artists/
    ├── {channelId}.txt
    ├── {artistId}.txt
    └── {artist_slug}.txt
```

---

## Slug & Normalization Rules

Filenames and folder names should follow these formatting rules:
* All lowercase letters (`a-z`) and digits (`0-9`).
* Replace all spaces, punctuation, dashes, and special characters with single underscores (`_`).
* Do not leave leading or trailing underscores.

| Entity | Original Name | Normalization Rule | Folder / File Slug |
| :--- | :--- | :--- | :--- |
| **Artist** | Michael Jackson | Lowercase + underscores | `michael_jackson` |
| **Artist** | AC/DC | Remove special characters | `ac_dc` |
| **Album** | Thriller | Lowercase + underscores | `thriller.txt` |
| **Album (Deluxe)** | Starboy (Deluxe Edition) | Strip parentheticals | `starboy.txt` |
| **Single** | Flowers - Single | Strip suffix or keep raw | `flowers.txt` or `flowers_single.txt` |
| **YouTube ID** | `OLAK5uy_l1U...` | Use exact ID case-preserved | `OLAK5uy_l1U....txt` |

---

## Path Resolution Priority

When an album or artist is opened in AvidTune, the client tries the following paths in order. The first file that exists and returns text will be displayed.

### 1. Albums, Singles, and EPs

AvidTune checks:
1. `albums/artists/{artist_slug}/{playlistId}.txt` *(Recommended for exact matches)*
2. `albums/artists/{artist_slug}/{norm_title}.txt`
3. `albums/artists/{artist_slug}/{full_title}.txt` *(Matches `..._single` or `..._deluxe`)*
4. `albums/artists/{artist_slug}/{albumId}.txt`
5. `albums/{playlistId}.txt`
6. `albums/{norm_title}.txt`
7. `albums/{albumId}.txt`

> **Note on Singles & EPs:** YouTube Music registers singles and EPs under the same album architecture. You can place single descriptions in either:
> * `albums/artists/{artist_slug}/{playlistId}.txt` (Most reliable)
> * `albums/artists/{artist_slug}/{track_name}.txt`

### 2. Artists

AvidTune checks:
1. `artists/{channelId}.txt` *(e.g. `artists/UCoIOOL7QKuBhQHVKL8y7BEQ.txt`)*
2. `artists/{artistId}.txt`
3. `artists/{artist_slug}.txt` *(e.g. `artists/the_weeknd.txt`)*

---

## File Examples

### Example 1: Artist Bio by Slug
**File path:** `artists/michael_jackson.txt`
```text
Michael Joseph Jackson was an American singer, songwriter, and dancer. Dubbed the "King of Pop", he is regarded as one of the most significant cultural figures of the 20th century.
```

### Example 2: Artist Bio by Channel ID (Avoids Name Collisions)
**File path:** `artists/UC0C-w0YjGpqDXGB8Uqc614A.txt`
```text
Official channel bio for Ed Sheeran...
```

### Example 3: Album by Artist and Title
**File path:** `albums/artists/daft_punk/random_access_memories.txt`
```text
Random Access Memories is the fourth and final studio album by the French electronic music duo Daft Punk, released on May 17, 2013 through Columbia Records.
```

### Example 4: Single by YouTube Playlist ID
**File path:** `albums/artists/miley_cyrus/OLAK5uy_mZ34jIe0LwR0m1_abc.txt`
```text
"Flowers" is a song by American singer Miley Cyrus, released on January 12, 2023, as the lead single from her eighth studio album, Endless Summer Vacation.
```

---

## Contribution Guidelines

1. **Format:** Files must be UTF-8 encoded plain text (`.txt`).
2. **Content:** Write encyclopedic, editorial, or background descriptions without spam, affiliate links, or profanity.
3. **Line Breaks:** Use standard double line breaks (`\n\n`) between paragraphs.
4. **Accuracy:** Prefer `playlistId.txt` (the ID starting with `OLAK5uy_...` from the album URL) or `channelId.txt` when creating descriptions to prevent collisions between different songs or artists with identical names.
