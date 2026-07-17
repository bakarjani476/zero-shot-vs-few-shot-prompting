# Raw Outputs & Per-Message Scoring

Ground truth: Praise, Question, Praise, Complaint, Question, Complaint, Question, Praise, Praise, Praise

## Raw Model Outputs

### Claude — Zero-shot
1. Complaint
2. Question
3. Complaint
4. Question
5. Question
6. Complaint
7. Complaint
8. Complaint
9. Complaint
10. Praise

### Claude — Few-shot
1. Complaint
2. Question
3. Praise
4. Question
5. Question
6. Complaint
7. Question
8. Complaint
9. Complaint
10. Praise

### ChatGPT — Zero-shot
1. Complaint
2. Question
3. Praise
4. Complaint
5. Question
6. Complaint
7. Question
8. Praise
9. Praise
10. Praise

### ChatGPT — Few-shot
1. Praise
2. Question
3. Praise
4. Complaint
5. Question
6. Praise
7. Question
8. Praise
9. Praise
10. Praise

### Gemini — Zero-shot
1. Complaint
2. Question
3. Complaint
4. Question
5. Question
6. Complaint
7. Complaint
8. Complaint
9. Complaint
10. Praise

### Gemini — Few-shot
1. Complaint
2. Question
3. Complaint
4. Question
5. Question
6. Complaint
7. Complaint
8. Complaint
9. Complaint
10. Praise

## Per-Message Scoring (✅ correct / ❌ incorrect)

| Msg | Ground Truth | Claude 0-shot | Claude few-shot | ChatGPT 0-shot | ChatGPT few-shot | Gemini 0-shot | Gemini few-shot |
|---|---|---|---|---|---|---|---|
| 1 | Praise | ❌ Complaint | ❌ Complaint | ❌ Complaint | ✅ Praise | ❌ Complaint | ❌ Complaint |
| 2 | Question | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 3 | Praise | ❌ Complaint | ✅ Praise | ✅ | ✅ | ❌ Complaint | ❌ Complaint |
| 4 | Complaint | ❌ Question | ❌ Question | ✅ | ✅ | ❌ Question | ❌ Question |
| 5 | Question | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| 6 | Complaint | ✅ | ✅ | ✅ | ❌ Praise | ✅ | ✅ |
| 7 | Question | ❌ Complaint | ✅ Question | ✅ | ✅ | ❌ Complaint | ❌ Complaint |
| 8 | Praise | ❌ Complaint | ❌ Complaint | ✅ | ✅ | ❌ Complaint | ❌ Complaint |
| 9 | Praise | ❌ Complaint | ❌ Complaint | ✅ | ✅ | ❌ Complaint | ❌ Complaint |
| 10 | Praise | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

## Accuracy Summary

| Tool | Zero-shot | Few-shot |
|---|---|---|
| Claude | 4/10 | 6/10 |
| ChatGPT | 9/10 | 9/10 |
| Gemini | 4/10 | 4/10 |
