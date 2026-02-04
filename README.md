# ⚽ CHOBO FRAPPE

**CHOBO FRAPPE** is a multiplayer soccer-inspired party game based on African street soccer culture.  
Players compete to avoid getting **nutmegged**, because getting nutmegged triggers hilarious slap-style punishment until reaching a safe zone.

This game is built with **Unity + C#**, focusing on fun mechanics, competitive chaos, and social multiplayer gameplay.

---

## 🎮 Game Overview

- **Title:** CHOBO FRAPPE  
- **Genre:** Sports / Party / Multiplayer  
- **Players:** 3–10  
- **Platform Target:** PC (Windows), Console potential  
- **Style:** Exaggerated African street soccer vibe with vibrant environments and humorous animations  

---

## 🕹️ Core Concept

Players try to outplay opponents by passing the ball between their legs (**nutmeg**).

When a player gets nutmegged:

- They trigger a slap/hit reaction animation  
- They must reach a **safe spot**  
- They may be eliminated depending on the mode  

---

## 🏆 Game Modes

### 🔥 Elimination Mode
- One nutmeg = instant elimination  
- Last player standing wins  

### 💪 Survival Mode
- Players start with **3 Health Points (HP)**  
- Nutmeg = −1 HP + slap animation  
- Eliminated when:
  - HP reaches 0  
  - Nutmegged 3 times  

---

## 🎮 Player Controls

| Action          | Input (Keyboard / Controller) |
|----------------|------------------------------|
| Move           | WASD / Left Stick            |
| Sprint         | Shift / Trigger              |
| Kick           | Space / Face Button          |
| Pass           | E / Shoulder Button          |
| Dribble Tricks | Q / Special                  |
| Dash Tackle    | Right Click / Trigger        |

---

## ⚙️ Gameplay Rules

### Nutmeg Detection
A nutmeg occurs when:

- The ball intersects between a player’s leg colliders  
- The ball’s movement vector confirms an opponent pass  

### Elimination Rules
- Nutmeg → eliminated immediately  

### Survival Rules
- Nutmeg → −1 HP  
- HP = 0 → eliminated  

---

## ❤️ UI Features

- Floating health bars  
- Nutmeg counter  
- Elimination announcements  

---

## 🛠️ Engine & Technology

### Recommended Engine: **Unity (C#)**

Unity is the best fit because:

- C# is beginner-friendly for rapid prototyping  
- Built-in physics helps ball + nutmeg detection  
- Mecanim animation system is powerful  
- Multiplayer frameworks are widely available  

### Alternative: Unreal Engine (C++)
For higher-end visuals and full customization.

---

## 🎭 Character & Animation Pipeline

### Character Creation Tools
- **Blender** (Free)
- Maya / 3DS Max (Industry standard)

### Animation Tools
- Mixamo (prebuilt soccer animations)
- Unity Asset Store animation packs
- Custom animations in Blender

### Animation Controller
Unity Animator system using:

- Blend trees (walk/run)
- Trigger events (kick/nutmeg/slap)
- State machines for transitions

---

## ⚽ Soccer Mechanics & Prebuilt Assets

Recommended Unity assets:

| Asset | Purpose |
|------|---------|
| Character Controller | Base movement |
| Soccer Game Kit | Ball physics + goal logic |
| Final IK | Realistic foot placement |
| Netcode / Mirror | Multiplayer synchronization |

---

## 💻 Technical Requirements

### Software

- Unity 2024+
- Visual Studio / Rider
- Blender (or Maya)
- Mixamo animations
- Git + GitHub
- Notion / Jira for team planning

### Hardware

- Development PC with real-time capable GPU  
- Windows devices for playtesting  

---

## 🚀 Development Roadmap

### Phase 1 — Prototype (4–6 weeks)
- Player movement  
- Ball physics  
- Nutmeg detection  
- Single-player test  

### Phase 2 — Core Modes (8–10 weeks)
- Elimination Mode  
- Survival Mode  
- UI + health system  

### Phase 3 — Multiplayer (10–14 weeks)
- Networked movement  
- Ball synchronization  
- Server-authoritative nutmeg validation  

### Phase 4 — Polish (8 weeks)
- Character models  
- Custom slap + celebration animations  
- Sound effects (soccer, crowd, slap hits)

---

## ⚠️ Key Technical Challenges

### Nutmeg Detection
- Scoped foot colliders  
- Ball intersection checks  
- Direction validation  

### Multiplayer Sync
Server-authoritative pattern:

- Server verifies nutmegs  
- Syncs ball + elimination states  

---

## 👥 Team Roles

| Role | Responsibilities |
|------|------------------|
| Game Designer | Rules, balancing, documentation |
| Programmer (C#) | Gameplay + networking |
| Animator | Rigs + slap/nutmeg reactions |
| Artist | Characters + environments |
| QA Tester | Playtesting + bug reporting |

---

## 🧩 Example Code: Nutmeg Detection (C#)

```csharp
void OnTriggerEnter(Collider other) {
    if(other.CompareTag("Ball") && IsBetweenLegs()) {
        RegisterNutmeg(attackerId, playerId);
    }
}

bool IsBetweenLegs() {
    Vector3 ballPos = ball.transform.position;
    return leftFoot.bounds.Contains(ballPos) &&
           rightFoot.bounds.Contains(ballPos);
}
