# Planning

## Community

I chose **r/LetsTalkMusic**, a Reddit community dedicated to in-depth discussions about music, albums, artists, and listening experiences. Unlike many music communities that focus on recommendations or news, posts in r/LetsTalkMusic encourage thoughtful conversations and detailed responses. Members frequently share personal experiences, explain musical concepts, offer advice, and discuss cultural or psychological aspects of music.

This community is a good fit for a text classification task because comments vary in **communicative intent** rather than simply sentiment. Two comments may both agree with the original poster, but one does so by telling a personal story while another provides an explanation or advice. This variety makes the classification task both meaningful and challenging.

---

## Labels

### Label 1: Personal Experience

**Definition:** A comment whose primary purpose is to share the author's own memories, listening habits, or personal experiences with music.

**Example 1**
> "I grew up in the 80's and 90's. We would get new albums and they would get played a lot. So I have memories from those times associated with those albums."

**Example 2**
> "All my best musical memories involve opening up a new LP, taking it out of the sleeve, putting it on the turntable, and listening to the full album for the first time."

---

### Label 2: Explanation / Interpretation

**Definition:** A comment whose primary purpose is to explain why a musical experience or phenomenon occurs using reasoning, psychology, history, or cultural context.

**Example 1**
> "It's a generational thing. Us old farts listened to albums because we bought albums."

**Example 2**
> "It's to do with the fact that the music you listened to in your teens and twenties coincides with a deeply formative time in your life."

---

### Label 3: Advice / Recommendation

**Definition:** A comment whose primary purpose is to recommend an action or suggest a different way of approaching music.

**Example 1**
> "Why do you not replay albums you like? Maybe you should slow down a bit. Listening to music isn't a race."

**Example 2**
> "Good albums need at least 3-4 listens before it really starts to make sense."

---

### Label 4: Agreement / Validation

**Definition:** A comment whose primary purpose is to affirm, validate, or reassure the original poster without providing substantial explanation or advice.

**Example 1**
> "Yes, but you're going to make new memories with the albums."

**Example 2**
> "Give it time though."

---

## Hard Edge Cases

Some comments naturally combine multiple discourse styles. For example:

> "Albums aren't like Pokémon, you don't have to listen to them all. If you like something go back and listen to it again. I've listened to many albums hundreds of times..."

This comment contains both **Advice** and **Personal Experience**.

To keep labels mutually exclusive, each comment will be assigned according to its **primary communicative intent**. If a comment begins with agreement but is mostly an explanation, it will be labeled **Explanation / Interpretation**. Likewise, if a comment contains advice but is primarily a personal story, it will be labeled **Personal Experience**.

---

## Data Collection Plan

I will collect comments from **r/LetsTalkMusic** using Reddit's API (PRAW). I plan to sample multiple discussion threads with high comment counts to capture a variety of discourse styles.

My goal is to collect approximately **200 labeled comments**, aiming for about **50 comments per label**.

If one label is underrepresented after collecting 200 comments, I will gather additional discussion threads where that discourse type is more common and continue sampling until the dataset is reasonably balanced.

---

## Evaluation Metrics

The classifier will be evaluated using three primary criteria:

- **Per-Class Accuracy** – Measure the accuracy for each label to ensure the model performs consistently across all discourse types.
- **Specificity (True Negative Rate)** – Measure how well the classifier avoids assigning incorrect labels, particularly between similar categories such as Personal Experience and Explanation.
- **Length Robustness** – Evaluate performance across short, medium, and long comments to ensure the classifier maintains consistent performance regardless of comment length.

---

## Definition of Success

The classifier will be considered successful if it can reliably identify the primary communicative intent of comments across all four categories.

A useful classifier should achieve:
- Strong per-class accuracy across all labels.
- High specificity with minimal confusion between similar discourse types.
- Consistent performance regardless of comment length.

Such performance would make the classifier useful for automatically organizing discussions, analyzing conversation patterns, or assisting moderators in understanding the types of responses within the community.
