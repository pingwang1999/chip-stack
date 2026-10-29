# AI Chip Packaging Stack

GB300 NVL72 rack › Compute tray › Package stack › Materials & suppliers

A signal leaving the GPU die crosses four carriers before it reaches the motherboard. Each one is built from a different material set, and each one has a different supply base. Click any layer to see what it is made of, who makes it, and where it binds.

_Updated 2026-10-23. Text edition of https://claude.ai/artifact/DNEcgGq9tbtRDWCmtWmnnt. Content is user-generated and unverified._

## Overview: four carriers, four material chains

PCB is often lumped in with chip packaging. It does not belong there. The substrate runs on build-up film with no glass reinforcement. The PCB runs on copper clad laminate, pressed from copper foil, resin and glass fabric. The two chains barely share a supplier.

The numbering is not a taxonomy. It is the order the signal actually travels. Moving outward from the die, pad pitch widens by roughly an order of magnitude at every step, and the material set changes with it. 01 is innermost, 04 is the board.

## Layer 01 — Die & HBM

_LOGIC DIE AND HIGH BANDWIDTH MEMORY · Silicon · TSV die stacking_

- **Full name:** Logic die and high bandwidth memory
- **Position:** Innermost layer, where the signal starts
- **Purpose:** Compute itself, plus memory sitting right next to it
- **Function:** Logic operations and data staging
- **Materials:** Silicon wafer. HBM is a vertical stack of DRAM dies joined by through-silicon vias

**Where it binds.** HBM is the only thing on this map that sits in layer 01 and layer 02 at the same time. It needs a leading-edge DRAM process to make the dies and advanced packaging to stack twelve of them, so its supply behaves unlike the rest of memory. Neither gate opening is enough on its own. Micron has put a number on that with its three-to-one input ratio, meaning HBM3E consumes roughly three times the wafer of DDR5 for the same capacity, and has said the ratio rises in later generations. Add 2026 supply already sold out against a stated ability to meet only half to two-thirds of customer demand, and the gap is not something capex alone closes.

### Suppliers

| Company | Ticker | Country | Component | Role | Concentration | Sole source |
|---|---|---|---|---|---|---|
| TSMC | 2330 | Taiwan | Logic die | Leading-edge logic foundry | high | no |
| SK hynix | 000660.KS | Korea | HBM | High bandwidth memory | medium | no |
| Samsung | 005930.KS | Korea | HBM | High bandwidth memory | medium | no |
| Micron | MU | USA | HBM | HBM and DRAM. 2026 supply fully sold out, with the company stating it can meet only half to two-thirds of customer demand | medium | no |
| Advanced Echem Materials | 4749 | Taiwan | Lithography materials | Sole supplier of a rinse surface modifier used by foundry customers on every node below 40nm | high | **yes** |
| Hanwha Semitech | 272210.KS | Korea | Stacking and bonding tools | SK hynix bonder partner. A commercial hybrid bonding launch depends on this class of equipment | medium | no |
| BE Semiconductor | BESI | Netherlands | Hybrid bonding tools | The main hybrid bonding equipment supplier, which is what stacking moves to after HBM4E | high | no |
| ASMPT | 0522.HK | Hong Kong | Thermocompression bonding tools | Thermocompression bonders, the tools behind today's mainstream HBM stacking | medium | no |
| Shin-Etsu Chemical | 4063.T | Japan | Silicon wafer | One of the two dominant wafer makers | high | no |
| SUMCO | 3436.T | Japan | Silicon wafer | One of the two dominant wafer makers | high | no |
| Tokyo Electron | 8035.T | Japan | Process equipment | Coat and develop, etch, deposition and thermal, so it spans several steps | medium | no |
| Kokusai Electric | 6525.T | Japan | Thermal process equipment | Oxidation and batch thermal furnaces | medium | no |
| ASML | ASML | Netherlands | Lithography equipment | The only source of EUV scanners anywhere, so every step down in linewidth runs through one company | high | **yes** |
| Lam Research | LRCX | USA | Etch and deposition | Etch and deposition. Deep via etch is what makes TSVs possible | high | no |
| Applied Materials | AMAT | USA | Deposition and metallisation | The largest supplier of thin film deposition and metal wiring tools | high | no |
| Advantest | 6857.T | Japan | Test equipment | A main supplier of memory and SoC testers | high | no |
| Teradyne | TER | USA | Test equipment | A main supplier of testers | medium | no |
| ChipMOS | 8150 | Taiwan | Memory test | Memory test and assembly. Wafer sort is the gate that finds the good dies before stacking | medium | no |

**Capacity notes**

- **TSMC:** Customer N2 utilisation tracking to 50% in 2Q26, 80% in 3Q26 and 100% in 4Q26, with N2 and N3 capacity up roughly 70% and 25% year on year
- **Micron:** FQ3 FY26 revenue around $42bn at over 81% gross margin, FQ4 guided near $50bn. $22bn of customer prepayments received and capex raised from $20bn to over $25bn. HBM4 revenue has passed $1bn and is ramping around twice as fast as HBM3E. 26 long-term agreements signed covering more than 35% of revenue to 2030, with more than 75% of 2027 output already committed. Singapore HBM advanced packaging starts in early 2027 and the Taiwan site ships mid-2027. Third of the three HBM suppliers by share
- **Advanced Echem Materials:** Kaohsiung phase one full by 1H27, phase two in volume mid-2027. Front-end semiconductor materials take three to five years from development through qualification

### Semiconductor front-end process

**HBM stack** (12 DRAM + 1 base die): A stack is only good if every die in it is good. Twelve dies in series is where the hard part of this chain lives. Suppliers: SK hynix, Samsung, Micron.

**The dies in a stack** (12 DRAM + 1 base die): A stack holds two kinds of die. Twelve are DRAM, made on a memory process in the memory makers' own fabs. The thirteenth is the base die at the bottom, carrying the external interface and control logic. From HBM4 it moves off the memory process onto a foundry logic process, which opens an external link in what used to be a closed memory chain.

| # | Step | What happens | Suppliers |
|---|---|---|---|
| 01 | Wafer manufacturing (Ingot, slicing, polishing) | Crystal growth, slicing, lapping and polish. HBM starts on the same silicon as any other DRAM. What changes is everything after. | Shin-Etsu Chemical, SUMCO |
| 02 | Oxidation (Silicon dioxide growth) | Growing a silicon dioxide layer for insulation and protection. Almost every later step builds on it. | Tokyo Electron, Kokusai Electric |
| 03 | Photolithography (Pattern transfer) | Projecting the circuit pattern onto resist. Linewidth is decided here, and EUV scanners come from exactly one company, which makes this the cleanest single point of dependency in the whole semiconductor chain. | ASML, Advanced Echem Materials |
| 04 | Etching (Material removal) | Removing what the resist does not protect. Through-silicon vias are cut by this class of process at aspect ratios far beyond ordinary structures, and it is part of why HBM takes longer in the fab. | Lam Research, Tokyo Electron |
| 05 | Deposition (Thin film growth) | Building dielectric and metal layers one at a time. More layers means more passes through this step. | Applied Materials, Lam Research, Tokyo Electron |
| 06 | Metal wiring (Interconnect) | Connecting the devices. HBM through-silicon vias have to be filled with copper, which is harder and slower than ordinary DRAM metallisation. | Applied Materials, Lam Research |
| 07 | Electric die sorting (Wafer test) | Testing on the wafer before dicing to find the good dies. This matters more for HBM than for anything else, because stacking a bad die scraps all twelve. | Advantest, Teradyne, ChipMOS |

## Layer 02 — Advanced packaging

_ADVANCED PACKAGING / COWOS · CoWoS · interposer · TSV_

- **Full name:** Advanced packaging, 2.5D integration
- **Position:** Between the die and the substrate
- **Purpose:** Puts the GPU die and several HBM stacks on one common base
- **Function:** Very short reach, very high bandwidth die-to-die interconnect
- **Materials:** Silicon interposer or redistribution layer, through-silicon vias, microbumps, underfill, molding compound

**Where it binds.** This is the layer the industry agrees has been tightest. What binds here is not process yield the way it would be in a fab. It is physical interposer capacity and the time it takes to stand up more of it.

### Suppliers

| Company | Ticker | Country | Component | Role | Concentration | Sole source |
|---|---|---|---|---|---|---|
| TSMC | 2330 | Taiwan | CoWoS | Interposer manufacturing and 2.5D integration | high | no |
| ASE | 3711 | Taiwan | OSAT | Back-end assembly and test | medium | no |
| Amkor | AMKR | USA | OSAT | Back-end assembly and test | medium | no |
| Jentech Precision | 3653 | Taiwan | Lids and stiffeners | Largest maker of package-level thermal hardware. GPU lids, heat spreaders and stiffener rings. Rubin content runs three to four times B300 |  | no |
| All Ring Tech | 6187 | Taiwan | Packaging equipment | Dispensing and inspection equipment for CoWoS, and the dispensing supplier for TSMC SoIC wafer-on-wafer |  | no |
| Intel | INTC | USA | EMIB packaging | The other 2.5D route besides CoWoS. The Google and MediaTek ASIC is reported to use EMIB-T |  | no |
| Powertech Technology | 6239 | Taiwan | Fan-out panel level | FOPLP entering pilot qualification, volume targeted for mid-2027, also developing HBM packaging for customers |  | no |
| AP Memory | 6531 | Taiwan | Silicon capacitors | Integrated passive device silicon capacitors, built at PSMC, working to qualify into EMIB and CoWoS packages |  | no |

**Capacity notes**

- **Jentech Precision:** One of four qualified suppliers for VR200 microchannel cold plates, alongside AVC, Cooler Master and Delta
- **All Ring Tech:** CoWoS and FoCoS equipment runs around 87% of 2026 revenue
- **Intel:** Advanced packaging capacity reported to double in each of 2027 and 2028
- **AP Memory:** IPD targeted at more than 35% of revenue next year

## Layer 03 — IC substrate

_IC SUBSTRATE / ABF · ABF film · no glass reinforcement_

- **Full name:** IC substrate, ABF substrate at the high end
- **Position:** Between the package and the board
- **Purpose:** Fans the fine package pitch out to something the board can actually attach to
- **Function:** Signal fan-out, mechanical support, part of the thermal path
- **Materials:** ABF build-up film carries no glass. The core layer is a glass-reinforced laminate. Plus copper foil, laser-drilled vias and solder balls

**Where it binds.** Substrate pricing moves on the same line as PCB. The core of an ABF substrate is itself a laminate, Kinsus is qualifying a T-glass plus E-glass build, and Elite Material has started shipping core material into substrates. So when glass fabric and copper foil tighten, substrates tighten with them. Unimicron and Ibiden capacity is absorbed by AI GPUs and ASICs, which is why the next-generation AMD server CPU substrate went to Nan Ya PCB.

### Suppliers

| Company | Ticker | Country | Component | Role | Concentration | Sole source |
|---|---|---|---|---|---|---|
| Ajinomoto | 2802.T | Japan | ABF build-up film | Build-up film. Essentially no qualified alternative | high | **yes** |
| Ibiden | 4062.T | Japan | ABF substrate | ABF substrate. Capacity absorbed by AI GPUs and ASICs while also carrying the Intel EMIB ramp | medium | no |
| Shinko Electric | 6967.T | Japan | ABF substrate | Substrate manufacturing | medium | no |
| Unimicron | 3037 | Taiwan | ABF substrate | ABF and BT substrate. Yangmei and Luzhu both full, with customers prepaying to reserve capacity | medium | no |
| Nan Ya PCB | 8046 | Taiwan | ABF substrate | ABF and BT substrate. Picks up AMD Venice from 1Q27 as Ibiden and Unimicron capacity is taken by AI | medium | no |
| Kinsus Interconnect | 3189 | Taiwan | ABF substrate | ABF substrate, expanding on the Nvidia Vera CPU ramp, estimated to take more than half of Vera in 2027 | medium | no |

**Capacity notes**

- **Unimicron:** Luzhu phase three starts 2H26, phase two volume in 2027, Yangmei fab two in 2028. Resonac and MGC price increases have been passed through. General-purpose servers account for an estimated 25-30% of ABF demand and AI servers 30-35%
- **Nan Ya PCB:** 2Q26 ABF utilisation 80-85%, BT full. Estimated to take more than half of Venice. ABF capacity up 5-10% in each of FY27 and FY28, mostly through debottlenecking. NT$46.8bn capex for a large-format CoPoS substrate fab, with the Chiayi site in volume around FY29
- **Kinsus Interconnect:** ABF capacity 40m units per month in FY26, 50m from 2Q27, 65m in FY28 and 80m in FY29. Qualifying a T-glass plus E-glass build. With T-glass, copper foil and ABF film all rising, quarterly price increases of 5-10% are expected

## Layer 04 — PCB motherboard

_PRINTED CIRCUIT BOARD · CCL · copper · glass · resin_

- **Full name:** Printed circuit board
- **Position:** Outermost carrier
- **Purpose:** Carries the modules, distributes power, routes signal off-board
- **Function:** Signal transmission and power delivery
- **Materials:** Copper clad laminate, pressed from copper foil, resin and glass fabric, bonded layer to layer with prepreg

**Where it binds.** The tightest input this year is not an exotic one. It is ordinary E-glass fabric, up more than 80% in the first half, which has held laminate makers at around 70-75% utilisation with order books they cannot fill. High-end copper foil tells the same story, with HVLP4 demand well above what the Japanese incumbents plus Co-Tech can put out. Look one step further up and the real gate is equipment. High-end looms are quoting into 2030 and treaters run 18 to 24 months, so how fast this layer expands is decided by the machine builders.

### Suppliers

| Company | Ticker | Country | Component | Role | Concentration | Sole source |
|---|---|---|---|---|---|---|
| Gold Circuit Electronics | 2368 | Taiwan | PCB | High layer count boards for servers and switches. Capacity up more than 25% since May and still short of demand | medium | no |
| Zhen Ding Technology | 4958 | Taiwan | Flexible PCB | Built on flex, now shifting weight toward IC substrate and server boards, with building 13 under construction and 16 in planning | low | no |
| ITEQ | 6213 | Taiwan | CCL | The volume laminate supplier for general-purpose servers, concentrated on E-glass with M6 to M7 resin systems, holding more than 60% of the AMD platform | medium | no |
| Elite Material | 2383 | Taiwan | CCL | The high-end laminate leader. M9 moving from single digit to double digit share of mix, and now shipping core material into ABF substrates | medium | no |
| Taiwan Union Technology | 6274 | Taiwan | CCL | High-end laminate. M7 and above is 36% of mix, utilisation full, M9 in final qualification | medium | no |
| Fu Chiao (1815) | 1815 | Taiwan | Glass fabric and yarn | Integrated from yarn through fabric. Low DK1, Low DK2 and Low CTE all in production, with Taiwan and Dongguan weaving full | medium | no |
| Nitto Boseki | 3110.T | Japan | Low-Dk glass fabric | High-end glass reinforcement | high | no |
| Mitsui Kinzoku | 5706.T | Japan | HVLP copper foil | The main Japanese HVLP supplier. Most of the installed base is still first generation, and usable capacity shrinks with every generation step | high | no |
| Furukawa Electric | 5801.T | Japan | HVLP copper foil | One of the two main HVLP4 sources, and where Elite Material takes most of its HVLP4 |  | no |
| Co-Tech Development | 8358 | Taiwan | HVLP copper foil | The Taiwanese HVLP foil maker, selling to Elite Material, Taiwan Union and ITEQ, ramping HVLP4 to close the Japanese shortfall |  | no |

**Capacity notes**

- **Gold Circuit Electronics:** Combined capacity measured at NT$9.4bn of output value, against NT$7.5bn in May. AI-related was 40-50% of 2Q26. ASIC customers may move from HLC to a mixed HDI plus HLC build
- **Zhen Ding Technology:** New capacity phased in from 2026 to 2030, with the company stating that expansion is contracted to customers. IC substrate estimated at 12% of revenue in 2027
- **ITEQ:** Monthly capacity around 5.4m sheets in 2025, on a path to roughly 5.7m, 6.3m, 8.3m and 9.2m sheets through 2029. The 2.85m sheets added at Wuxi are dedicated to M7 and above. Utilisation held at 70-75% by E-glass supply. Industry treater lead times run 18 to 24 months. 4Q26 pricing up a further 15-20%, with fabric suppliers releasing small volumes that should lift utilisation toward 80%
- **Elite Material:** 3Q26 revenue NT$60.9bn. 4Q26 pricing up 5-10% on average, with the steeper increases at M6 and below. High-end capacity expected to add 3.15m sheets per month in 2027. Substrate material was historically BT-based and under 1% of revenue
- **Taiwan Union Technology:** 2.6m sheets per month exiting 2Q26, adding 600k each at Changshu and Thailand, reaching 3.8m by the end of 2027
- **Fu Chiao (1815):** Two furnaces plus four electric furnaces and 920 looms. Thailand phase one of 400 looms starts in 3Q27 with initial output already reserved by customers, expanding to 500 in 2028. Toyota automatic looms for high-end fabric are quoting delivery into 2030. July pricing up 30% on E-glass and 15% on Low DK2
- **Mitsui Kinzoku:** Around 620 t per month, predominantly HVLP1. Converted entirely to HVLP4 that same line yields only 320 t. Total capacity rises to 840 t after September 2026, which is still only 400-430 t if all of it runs HVLP4
- **Furukawa Electric:** Mitsui and Furukawa combined ran roughly 350 t per month of HVLP4 in 2025, expanding to 450-550 t by the end of 2026, against 2026 demand of about 1,200 t per month
- **Co-Tech Development:** 250 t per month across all foil, with 480 t of headroom at the third Yunlin plant. HVLP4 at 50-100 t per month, expected to reach 200-250 t during 2026. Foil equipment lead times run six months or more and new capacity takes 18 to 24 months to come online

### AI high-end PCB cost breakdown

| Item | Share of parent | Share of total PCB cost | Suppliers |
|---|---|---|---|
| AI high-end PCB | 100% | 100% | Gold Circuit Electronics, Zhen Ding Technology |
| Copper clad laminate | 45–60% of AI high-end PCB | 45–60% | ITEQ, Elite Material, Taiwan Union Technology |
| Copper foil | 40% of Copper clad laminate | 18–24% | Mitsui Kinzoku, Furukawa Electric, Co-Tech Development |
| Epoxy resin | 25% of Copper clad laminate | 11–15% | — |
| Glass fabric | 20% of Copper clad laminate | 9–12% | Fu Chiao (1815), Nitto Boseki |
| Other | 15% of Copper clad laminate | 7–9% | — |

### Demand amplification from a laminate grade step

CCL demand vs M6 = layer multiplier × area multiplier × yield-loss multiplier.

| Scenario | Layers | Layer × | Area × | Yield loss × | CCL demand vs M6 |
|---|---|---|---|---|---|
| M6 baseline | 12–16 | 1× | 1× | 1× | 1× |
| M8 base case | 24–32 | 2× | 2–2.5× | 1.15–1.3× | 4.6–6.5× |
| M8 GB300 largest board, upper bound | 40 | 2.5–3.33× | 3–5× | 1.15–1.3× | 8.6–21.6× |

- **M8 base case:** Layer counts pair 12 to 24 and 16 to 32, not crosswise. Doubling layer count also doubles board thickness.
- **M8 GB300 largest board, upper bound:** 8.6 to 16.3× off a 16-layer base, 11.5 to 21.6× off a 12-layer base. This assumes three extremes land together, so it is a bound rather than a forecast and should be read separately from the base case.

Layer count is set by the design and is effectively known. Yield and size are the only two variables that move with process maturity, so those are the two questions that decide where in the range a programme lands.

## Single-source dependencies

- **Advanced Echem Materials** (4749, Taiwan), Lithography materials: Sole supplier of a rinse surface modifier used by foundry customers on every node below 40nm
- **ASML** (ASML, Netherlands), Lithography equipment: The only source of EUV scanners anywhere, so every step down in linewidth runs through one company
- **Ajinomoto** (2802.T, Japan), ABF build-up film: Build-up film. Essentially no qualified alternative

## HBM demand cascade

Pick a rack, set how many ship in a year, and the chain works down to the HBM stacks and DRAM dies behind them. The number you set is a scenario, not a forecast.

Formula: racks × GPUs per rack × stacks per GPU = HBM stacks; × dies per stack = DRAM dies. Capacity = racks × GPUs × GB per GPU (1 PB = 10^6 GB); bits = GB × 8 (1 Eb = 10^9 Gb). LPDDR5X = racks × CPUs × GB per CPU.

| Rack | Gen | Status | GPUs/rack | HBM | GB/GPU | Stacks/GPU | Dies/stack | GB/stack | CPUs/rack | LPDDR5X GB/CPU |
|---|---|---|---|---|---|---|---|---|---|---|
| GB200 NVL72 | Blackwell | in production | 72 | HBM3E | 192 | 8 | 8 | 24 | 36 | 480 |
| GB300 NVL72 | Blackwell Ultra | in production | 72 | HBM3E | 288 (279 usable) | 8 | 12 | 36 | 36 | 480 |
| Vera Rubin NVL72 | Rubin | 2H 2026 | 72 | HBM4 | 288 | 8 | 12 | 36 | 36 | — |
| Rubin Ultra NVL576 | Rubin Ultra | 2H 2027, spec not final | 144 | HBM4E | 1024 | 16 | 16 | 64 | 36 | — |

| Rack | Racks/yr | HBM stacks | DRAM dies | HBM capacity | HBM bits | LPDDR5X capacity | LPDDR5X bits |
|---|---|---|---|---|---|---|---|
| GB200 NVL72 | 5,000 | 2,880,000 | 23,040,000 | 69.1 PB | 0.55 Eb | 86.4 PB | 0.69 Eb |
| GB200 NVL72 | 20,000 | 11,520,000 | 92,160,000 | 276.5 PB | 2.21 Eb | 345.6 PB | 2.76 Eb |
| GB200 NVL72 | 50,000 | 28,800,000 | 230,400,000 | 691.2 PB | 5.53 Eb | 864.0 PB | 6.91 Eb |
| GB300 NVL72 | 5,000 | 2,880,000 | 34,560,000 | 103.7 PB | 0.83 Eb | 86.4 PB | 0.69 Eb |
| GB300 NVL72 | 20,000 | 11,520,000 | 138,240,000 | 414.7 PB | 3.32 Eb | 345.6 PB | 2.76 Eb |
| GB300 NVL72 | 50,000 | 28,800,000 | 345,600,000 | 1,036.8 PB | 8.29 Eb | 864.0 PB | 6.91 Eb |
| Vera Rubin NVL72 | 5,000 | 2,880,000 | 34,560,000 | 103.7 PB | 0.83 Eb | — | — |
| Vera Rubin NVL72 | 20,000 | 11,520,000 | 138,240,000 | 414.7 PB | 3.32 Eb | — | — |
| Vera Rubin NVL72 | 50,000 | 28,800,000 | 345,600,000 | 1,036.8 PB | 8.29 Eb | — | — |
| Rubin Ultra NVL576 | 5,000 | 11,520,000 | 184,320,000 | 737.3 PB | 5.90 Eb | — | — |
| Rubin Ultra NVL576 | 20,000 | 46,080,000 | 737,280,000 | 2,949.1 PB | 23.59 Eb | — | — |
| Rubin Ultra NVL576 | 50,000 | 115,200,000 | 1,843,200,000 | 7,372.8 PB | 58.98 Eb | — | — |

Memory makers size demand in bits, not units. Die density changes every node, so only bits compare across generations. 1 Eb is a billion Gb.

The same rack also consumes LPDDR5X on the CPU side. In bits the two are close in size, but HBM burns several times the wafer per bit, which is where the gap opens once you convert to capacity.

**GB200 NVL72.** The first NVL72 rack. 192 GB per GPU works out to roughly 13.8 TB across the rack. _Basis: Capacity per GPU is public spec. Eight stacks per GPU and eight dies per stack are derived from capacity divided by the generation's per-stack size, not disclosed figures_

**GB300 NVL72.** Physically each GPU sits next to 8 HBM3E stacks, 12 layers each at 3 GB a layer, which is 288 GB. That is what the memory maker actually ships. NVIDIA's spec page lists 279 GB, the capacity a user can address, and 279 times 72 is exactly the 20 TB it quotes for the rack. The missing 9 GB is not explained officially. Industry reading points to reserved capacity or a layer switched off for yield, neither confirmed. The cascade uses 288, because that 9 GB of silicon still got made. _Basis: 72 GPUs and 20 TB per rack come from NVIDIA's rack spec page. 288 GB per GPU comes from NVIDIA's enterprise reference architecture, which separately lists 2304 GB across an eight-GPU baseboard, and 2304 divided by eight is exactly 288. The 36 GB, 12-high, 24 Gb-per-die stack is Micron's own HBM3E product specification, confirmed by a TechInsights teardown of a physical B300 package. Neither company states stacks per GPU. Eight falls out of 288 divided by 36, so it is not an assumption but two companies' published figures reconciling._

**Vera Rubin NVL72.** Moves to HBM4, where the interface doubles from 1024 to 2048 bits. The GPU package is a dual-die design and the rack carries 20.7 TB, which divided by 72 is about 288 GB, so this generation shows none of the gap between physical and usable capacity that GB300 does. Micron has announced HBM4 in high volume production for Vera Rubin. _Basis: 288 GB per GPU and 20.7 TB per rack are public reporting. The 36 GB 12-high stack is from Micron's HBM4 volume production announcement. Eight stacks follows from 288 divided by 36. Micron is also sampling a 48 GB 16-high part, and a switch to that would change the stack count per GPU._

**Rubin Ultra NVL576.** NVL576 counts 576 compute dies at four dies per package, so there are 144 packages. Each package carries 1 TB of HBM4E. This generation is still moving, so treat the numbers as order of magnitude. _Basis: Forward-looking public reporting, not final. Stacks and dies per stack are derived, not disclosed_

## About this map

**What this is.** A working map of the AI chip packaging supply chain, built bottom-up from company filings and sell-side research on the Taiwan and Japan supply base. The cost model on the PCB layer is my own derivation.

**Where it goes next.** Impact analysis. Each node carries concentration, sole-source status and qualification lead time, so a capacity or pricing event can be traced through to how many racks it gates and how long a substitution would take.
