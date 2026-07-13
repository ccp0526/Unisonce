# Unisonce 🧩

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/50dc24da-4f19-40fd-8d11-c337f6831b88" />

## 🎮 Game Overview
**Unisonce** is a 3D first-person puzzle game developed as a Final Year Project. The game explores the concept of psychological defense mechanisms through environmental puzzle-solving. 

Players must navigate complex spatial puzzles by utilizing the **"Blind Switch"** mechanic—seamlessly transitioning between the real world and a parallel reality controlled by a "Protector" persona.

## ✨ Core Mechanics
* **Blind Switch:** Instantly shift between two parallel dimensions at the press of a button to bypass obstacles and alter the environment.
* **Dual Objects (Spatial State-Tracking):** Interact with objects that exist across both realities but behave differently. For example, a pressure plate triggered in the real world might activate a hidden pathway in the Protector's world.

<img width="800" height="450" alt="BlindSwitch" src="https://github.com/user-attachments/assets/f78ef7aa-4262-4d03-87b4-c946255c64c2" />

---

## 🧠 Technical Showcase & Thought Process

As a Gameplay Programmer, my focus was on building scalable architecture and solving technical bottlenecks to ensure a smooth player experience. 

### 1. Achieving Zero-Latency Parallel World Switching
**The Challenge:** 
The core "Blind Switch" mechanic required players to transition between two vastly different environments instantly. Any loading screens, frame drops, or noticeable latency would ruin the immersion and gameplay flow.

**My Approach:**
Initially, Level Streaming seemed like the standard approach for managing multiple environments. However, loading/unloading levels inherently introduced a slight delay. 

To achieve true zero-latency, I designed a highly optimized **Hide/Show Spatial System** utilizing strict Object-Oriented Programming (OOP) principles:
* I engineered a base `DualObject` class.
* Instead of unloading the world, all objects for both realities are loaded simultaneously in the memory.
* An Event Dispatcher listens for the player's "Switch" input. Upon triggering, the system dynamically toggles the visibility (Render State) and collision profiles (Collision Enabled/Disabled) of all relevant `DualObject` instances in real-time.
* This approach ensures a seamless, instantaneous transition while maintaining stable 3D lighting and a high frame rate. Adding new puzzle elements simply requires inheriting from this base class, making the codebase highly scalable.

<img width="1090" height="652" alt="image" src="https://github.com/user-attachments/assets/3434be23-f2e2-4eaa-8b65-6f0c16e49cc6" />

### 2. Overcoming Art Resource Limitations as a Programmer
**The Challenge:** 
Creating or sourcing two entirely different sets of cohesive 3D assets to clearly separate the "Real World" from the "Protector World" was a major bottleneck for the project's scope, especially as a programmer focused on system logic rather than 3D modeling.

**My Approach:**
Instead of relying purely on unique 3D models to differentiate the worlds, I leaned into **Technical Art and Engine Features** to solve visual problems through logic:
* **Smart Asset Utilization & Material Swapping:** I sourced a cohesive base asset pack but utilized Unreal Engine's Material Instancing system. During the "Blind Switch," my system doesn't just swap objects; it dynamically swaps Material Instances and alters lighting setups to instantly change the atmosphere of the same base geometry.
* **Post-Processing & Visual Feedback:** To ensure players immediately understand which reality they are in, I programmed global post-process transitions (like color grading and exposure shifts) and specific particle effects that trigger upon state switching. This compensated for the lack of bespoke models and ensured high gameplay readability.

<img width="1643" height="472" alt="image" src="https://github.com/user-attachments/assets/9d9f4aa3-6818-44f5-9e7d-0e07de7317b5" />

---

## 🛠️ Tech Stack & Details
* **Engine:** Unreal Engine 5
* **Languages:** C++, Blueprints
* **Role:** Gameplay Programmer (Systems Architecture, Physics Interactions, State Machines, Tech Art Integration)
* **Development Duration:** Nov 2025 - July 2026
