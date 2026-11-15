# KNN_Wafer(IDSE_Project_Game)
# 🦌🦏 Savanna Guard: Acoustic KNN & Precision Tagging Engine

An interactive browser game that teaches the **K-Nearest Neighbors (KNN)** classification algorithm. You fly a ranger drone over a savanna, lock onto mystery bushes (`?`), watch KNN vote in real time, and fire the correct tranquilizer dart (Light for Gazelle, Heavy for Rhino).

Everything is in a single HTML file. No installation or build step is needed.

---

## 🚀 How to play

Open Game_Link.md and open the link provided and play

## 🎯 Objective

Each wave has several mystery bushes. Every bush hides either a **Gazelle** or a **Rhino**. Use the KNN vote to decide which dart to fire.

| Result | Score |
|---|---|
| Correct dart | **+100** |
| Wrong dart | **−40** (score never drops below 0) |

The HUD tracks your score, accuracy and a live **confusion matrix**.

---

## 🕹️ How to Play

1. **Choose a wave** from the top bar.
2. **Lock a target.** Click a `?` bush, or press **🎯 Next Mystery**.
3. **Read the KNN vote** (top-right panel). Lines connect the bush to its K nearest known animals, ranked #1 to #K.
4. **Tune K** with the Neighbors slider or the `-` / `+` buttons.
5. **Pick the dart.** Light 🦌 or Heavy 🦏, or leave **Auto-KNN** on to follow the vote automatically.
6. **Adjust the Aim Angle** (the curve of the dart's flight path).
7. **Fire!** Press **🎯 FIRE DART** or the Space bar.

Correctly tagged animals are added to the known dataset, so later predictions improve (a simple form of active learning).

---

## ⌨️ Controls

| Action | Control |
|---|---|
| Move drone | Joystick, **A / D**, or **← / →** |
| Lock a mystery bush | Click / tap the `?` bush |
| Next target | **🎯 Next Mystery** button |
| Fire dart | **Space** or **FIRE DART** button |
| Drag-to-aim | Drag on the canvas and release to fire |
| Change K | Slider or `-` / `+` (odd values 1–13) |
| Aim angle | Slider or `-` / `+` (−55° dive to +45° loft) |
| Show or hide KNN zones | **Zones** checkbox |
| Mute or unmute | 🔊 button |
| Restart the current wave | **RESET** button |

---

## 🌍 The Three Waves

| Wave | Scenario | What it teaches |
|---|---|---|
| **1. Clear Plains** | Gazelles and Rhinos in well-separated territories | K = 3 or 5 works cleanly |
| **2. Outlier Valley** | A stray rhino and a stray gazelle sit in the wrong zones | **K = 1 overfits** and gets fooled by outliers |
| **3. Herd Imbalance** | 16 Gazelles vs only 4 Rhinos | **A very large K (11–13)** drowns out the minority class |

---

## 🧠 The Data Science Behind It

- **Features:** each animal has two acoustic features, **mass** (horizontal position) and **frequency** (vertical position).
- **Distance:** Euclidean distance in the (mass, frequency) feature space.
- **Prediction:** the K closest known animals vote and the majority wins.
- **Bias–variance trade-off:**
  - K = 1 gives high variance (overfitting).
  - K = 11–13 gives high bias (over-smoothing).
  - K = 3–9 is usually balanced.
- **Decision boundary:** the **Zones** overlay shades the map green (Gazelle) or amber (Rhino) to show what KNN would predict at each point.
- **Confusion matrix:** shows True Gazelle, True Rhino and Wrong Dart counts, plus overall accuracy.
- **Class imbalance:** Wave 3 shows how a majority class can dominate the vote.

---

## 💡 Learning Challenges

- Beat Wave 2 with K = 1, then again with K = 5. What changes?
- Find the K value where Wave 3 starts misclassifying Rhinos.
- Turn off **Auto-KNN** and try to beat the algorithm using your own judgment.

---
