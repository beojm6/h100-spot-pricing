# Cheap GPU Cloud: H100 Hours From $1.19, What Spot and Community Tiers Really Cost, and Where Vultr Fits In

The same NVIDIA H100 rents for **$1.19 an hour** at the cheapest guaranteed rate available right now, and for **$12.29 an hour** on Azure. Same chip, roughly ten times the price. Everything between those two numbers is the cheap GPU cloud decision in miniature: which provider actually charges the low rate, which billing tier quietly eats the savings, and how to match a provider to the way your workload runs.

Most of the usable market sits between $2 and $3.50 an hour for on-demand H100 time. Vultr lands at roughly $2.00–$2.50 with global region coverage, which puts it in the cheapest mainstream band. Every rate below was checked against the market in mid-August 2026 and will move, so treat each one as a starting point rather than a contract.

> **Short version:** if you want datacenter GPUs on demand with a normal dashboard and regions worldwide, Vultr's H100 runs around **$2.00–$2.50 an hour** (independent tracker range), billed hourly with charges that stop once they add up to the monthly price. 👉 [Check Vultr's current GPU rates](https://www.vultr.com/pricing/?ref=7268283) If you'd rather chase the absolute floor, marketplace tiers start near $0.02 an hour for consumer cards — the section on preemption explains what that costs you in retries.

## What a cheap GPU cloud actually costs right now

The cheapest guaranteed H100 is $1.19 an hour. The next guaranteed rate is $1.68. Everything below $2 beyond those two is either an auction, a peer marketplace listing, or an interruptible tier that someone else can reclaim.

The market sorts itself into four tiers. Hyperscalers (AWS, Google Cloud, Azure) charge $6.88 to $12.29 per H100-hour on demand and justify it with managed services and enterprise paperwork. Specialty clouds (Lambda, CoreWeave, Together AI) sit mid-table with better multi-node networking. Long-tail and regional providers — Vultr, Voltage Park, Lyceum, Hetzner Cloud — cluster between $1.99 and $2.50. Decentralized marketplaces go lowest of all, with the most variance.

| Provider | Cheapest H100 rate | How it bills | The catch |
| --- | --- | --- | --- |
| Compute Cheap | **$1.19/hr** reserved ($1.15 interruptible) | Prepaid blocks of 2,000+ GPU-hours | US and EU only; B200 and GB300 currently sold out |
| Vast.ai | $1.33–$2.00/hr (listing range, median $2.00) | Per-second peer marketplace | Each host sets its own uptime and terms |
| Latitude.sh | $1.68/hr | Hourly bare-metal | Single-GPU H100 only, no H200; 8× B300 node is $64/hr |
| SF Compute | ~$1.95/hr average clearing price | Hourly auction for whole 8-GPU nodes | An auction price you can't lock in; SLA sits behind a login |
| Voltage Park | $1.99/hr | On-demand, Ethernet networking | US only; InfiniBand, H200 and Blackwell are quote-only |
| Vultr | **~$2.00–$2.50/hr** (tracker range) | Hourly, capped at the monthly rate | Not the floor, but global regions and plain hourly billing |
| Hetzner Cloud | $2.10–$2.50/hr (tracker range) | On-demand | Germany/EU focus |
| Prime Intellect | From $2.43/hr (spot from $0.94) | Aggregator of 50+ clouds | Quality varies with the host behind each listing |
| RunPod | $2.69/hr Community, $3.29 Secure | Per-second billing | Community tier can be preempted |
| Lyceum | $2.79/hr ($1.10 spot) | Per-second billing | EU only: Denmark, France, Germany |
| Nebius | $3.85/hr ($2.15 preemptible) | Per-second billing | H100 capacity is Finland-only; US regions carry H200/B200 |
| Lambda | $3.99/hr for 8× H100 SXM ($4.29 single GPU) | Per-minute billing | No H200 on the price page |
| CoreWeave | $6.16/hr per H100 ($2.46 spot) | 8-GPU nodes, up to 60% off committed contracts | Three-year minimum term since April |
| AWS | $6.88/hr per GPU on p5 ($2.59 spot) | On-demand, spot, Capacity Blocks at $5.19 | Egress billed on top |
| Google Cloud | $10.98/hr per GPU (a3-highgpu-8g) | On-demand | Newer A3 tiers are commitment-only |
| Azure | $12.29/hr per GPU ($2.27 spot) | On-demand, spot | Highest list price in this table |

One footnote to the table: marketplace listings built on consumer cards (Vast.ai from $0.02, Salad's RTX 3090 from $0.09) sit below every datacenter row because they're a different hardware class entirely. More on those near the end.

## The sub-$1 GPU instances are usually a hardware trap

Yes, AWS and Azure both rent a GPU for $0.526 an hour (g4dn.xlarge and NC4as_T4_v3 respectively), and Google Cloud's g2-standard-4 is $0.71. All three are T4 cards from 2018. A RunPod RTX A5000 at $0.16 an hour delivers more throughput than a T4 at $0.53, which tells you how dated that hardware is.

Compare within the same GPU class and the hyperscaler premium lands at 3–5×: an 8× H100 node runs $55.04/hour on AWS p5 and $88.49/hour on Google Cloud's a3-highgpu-8g, against roughly $2–$3 per GPU-hour at the long-tail providers in the table above. The big three earn their keep through SageMaker-style managed tooling and procurement-friendly contracts. If what you want is raw GPU hours at the best rate, filter by GPU class first and price second.

## Where Vultr fits in the cheap GPU cloud market

Vultr is the mainstream face of the long-tail tier: on-demand H100 tracked at $2.00–$2.50 an hour, regions worldwide, and billing that behaves. An independent GPU price index put it there earlier this year — inside the cheapest band of the market and well clear of hyperscaler pricing. Rates move, so the current number lives on Vultr's own GPU page — 👉 [see Vultr's cloud GPU plans and hourly rates](https://www.vultr.com/products/cloud-gpu/?ref=7268283) before anything in this section goes stale.

Two things make it a practical default for a lot of teams. The first is billing: instances accrue hourly and the charges stop once they add up to the flat monthly price. A GPU running 24/7 costs exactly the listed monthly rate; one running four hours a day costs about a sixth of it. Spiky workloads stay predictable without a bidding strategy. The second is scope: compute, storage and GPU under one account and one bill, with regions spread across North America, Europe, Asia-Pacific and beyond, so you can move a workload closer to users without changing vendors.

Who it's not for. If you're hunting the absolute floor, marketplaces undercut Vultr by design — Vast.ai listings and Salad's batch tier exist to clear inventory at commodity prices, and you accept the variance. If you need 8-GPU InfiniBand clusters on committed terms, the node-sellers in the mid-table handle that better. Vultr's lane is the unglamorous middle: datacenter GPUs, sane billing, no auction.

The lineup covers the usual datacenter spread, with the H100 as the anchor rate and the smaller cards running proportionally less:

| GPU | VRAM | Sweet spot | Rent |
| --- | --- | --- | --- |
| NVIDIA H100 | 80 GB | FP8 inference, fine-tuning, larger training runs | [Check rate & rent](https://www.vultr.com/products/cloud-gpu/?ref=7268283) |
| NVIDIA A100 | up to 80 GB | Training and inference that don't need FP8 | [Check rate & rent](https://www.vultr.com/products/cloud-gpu/?ref=7268283) |
| NVIDIA L40S | 48 GB | Image and video inference, cost-sensitive serving | [Check rate & rent](https://www.vultr.com/products/cloud-gpu/?ref=7268283) |
| NVIDIA A16 | 16 GB per GPU | Light inference, dev and test boxes | [Check rate & rent](https://www.vultr.com/products/cloud-gpu/?ref=7268283) |

## What the cheapest tiers actually cost you in retries

Cheap tiers get cheap by letting someone else take the hardware back. That's the whole deal.

Here's the math for a job that needs 20 GPU-hours of real compute, checkpoints every 30 minutes, on an interruptible instance that gets reclaimed roughly every three hours. Each preemption throws away up to half an hour of work, then costs another 10–15 minutes to land a new node and reload the weights. Across the run that's about 7 preemptions, 1.7 hours of recomputed work, and 17% more wall-clock time.

| Tier | Rate | Billed hours | Total | Wall-clock |
| --- | --- | --- | --- | --- |
| Interruptible / community | $0.18/hr | ~22.3 h | **~$4.00** | ~23.3 h |
| On-demand / secure | $0.35/hr | 20 h | $7.00 | 20 h |

Interruptible still wins on money, and usually will — but only if checkpoint-and-resume actually works in your code. Saving $3 isn't worth an engineering afternoon unless the job runs repeatedly or at much larger scale. The working rule: batch, repeated, restartable jobs go on the cheap tier; a demo due tomorrow morning or an inference endpoint with users on it goes on the secure tier.

Spot pricing follows the same logic with bigger spreads. Azure charges $12.29 on demand for its H100 and $2.27 on spot, the steepest on-demand-to-spot gap in the table, with eviction risk to match. Across long-tail providers, spot H100 runs $0.80–$1.50, A100 $0.40–$0.70, H200 $1.20–$2.00 with thin availability. Spot is the wrong tool for user-facing serving, tight deadlines, and anything where eviction loses unrecoverable state.

Bursty inference has its own trap: idle hours. A $0.16/hour instance running around the clock costs $3.84 a day whether requests arrive or not. Serverless GPU platforms bill per second and scale to zero, which removes idle cost entirely at the price of a cold-start penalty on the first request after scale-down. Once utilization climbs past roughly a third of the day, a cheap always-on instance wins again.

## Reserved capacity: the cheapest production-grade GPU access

For predictable workloads, reserving beats everything except owning hardware. Three-year reserved H100 at long-tail providers runs **$1.30–$1.80 an hour**, 30–50% below their own on-demand rates, and lands within roughly 15% of owned-cluster economics without the operational burden. A100 reservations drop to $0.55–$0.75 an hour on three-year terms.

Concrete reference points from the table above: Compute Cheap sells reserved H100 at $1.19 in prepaid blocks of 2,000 GPU-hours or more with a 99.9% uptime SLA, though its B200 and GB300 capacity is currently sold out. CoreWeave discounts committed contracts by up to 60%, but since April the minimum term is three years — a real commitment, not a quarterly one.

The decision rule is blunt. If the same workload will run for months, collect reservation quotes and compare them against your on-demand math. If the workload might change shape next month, reservations are how you end up paying for capacity you stop using.

## Consumer-GPU marketplaces: the absolute floor

If the workload tolerates consumer cards, the floor is measured in cents. Vast.ai lists RTX 3090 and 4090 capacity from $0.02 an hour alongside datacenter cards, with per-second billing; its H100 listings ran $1.33 to a $2.00 median on the day prices were checked. SaladCloud rents RTX 3090 from $0.09 an hour, bills per second, and splits pricing into priority tiers: High priority is never preempted by other workloads, while the Lowest (Batch) tier is the cheap lane for retryable jobs and stateless inference behind a queue.

These marketplaces suit rendering farms, batch transcription, and any stateless pipeline that shrugs when a node disappears. For always-on production, budget 50–80% above the sticker price for secure or on-demand tiers, or start with an owned cloud instead.

## How to choose, by workload

Map the job to the tier first, then compare brands within it:

- **Always-on, user-facing inference:** on-demand secure tier or a reservation. Vultr sits at the cheap end of that lane; Verda and Lyceum cover EU data-residency needs.
- **Fine-tuning with working checkpoints:** spot or interruptible, $0.80–$1.50 for H100 time.
- **Bursty endpoint below a third-of-the-day utilization:** serverless with scale-to-zero. Above that line, a cheap always-on instance.
- **Months of predictable training:** three-year reserved H100 at $1.30–$1.80.
- **Need H200 now:** long-tail on-demand runs $2.50–$3.50; Prime Intellect listings span $0.47–$3.14, so vet the host behind each one.
- **Want datacenter GPUs without marketplace roulette:** that's Vultr's lane at $2.00–$2.50 for H100 — 👉 [browse Vultr's plans and regions](https://bit.ly/VulTR) to see how the lineup maps to your workload.

## Cheap GPU cloud FAQ

### What is the cheapest H100 cloud right now?
Compute Cheap at $1.19 an hour reserved ($1.15 interruptible), per the mid-August price check. Latitude.sh is the next guaranteed rate at $1.68. Below that, only marketplace and auction pricing exists, and none of it is guaranteed.

### Are AWS, Azure, or Google Cloud ever the cheapest option?
On spot, sometimes. Azure's H100 spot rate is $2.27 versus $12.29 on demand. For raw on-demand GPU hours, the big three run 3–5× the long-tail providers once you match GPU class, and AWS bills egress on top of p5 pricing.

### Is a $0.02 per hour GPU actually usable?
For consumer-card workloads, yes — with per-second billing and preemption as the default condition. It fits rendering, batch jobs, and stateless inference behind a queue. It does not fit an always-on production endpoint.

### Does Vultr have cheap GPUs?
By mainstream-cloud standards, yes: an independent price index tracked its on-demand H100 at $2.00–$2.50 an hour, with hourly billing capped at the monthly rate and regions worldwide. Confirm the current rate on Vultr's pricing page, since these numbers move.

### What does an H200 cost on a budget?
Long-tail providers run $2.50–$3.50 on demand, and three-year reservations drop to $1.80–$2.50. Supply is tighter than H100 through 2026, so availability is the bigger constraint than price.

## Before you rent

Two questions settle most of this. How many hours a day will the GPU actually run? And does your code survive a preemption? Spiky usage plus no checkpointing points to serverless or a cheap always-on instance you can afford to leave running. Round-the-clock usage for months points to a reservation quote. Everything else is comparing rates within the tier you've already chosen, plus one last check on egress pricing if you'll move large datasets out constantly — some providers bill that on top of compute.

If the unglamorous middle is where you've landed, 👉 [check today's GPU rates on Vultr](https://www.vultr.com/pricing/?ref=7268283) and see how the current H100 price fits your math.
