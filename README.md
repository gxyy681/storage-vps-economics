# Cheap Storage VPS: What 1 TB Costs Per Month, Why $/TB Falls as Disks Grow, and When Transfer Becomes the Real Bill

One terabyte of usable disk starts at $5 a month. HostHatch's 1 TB storage VM includes 2,500 GB of transfer at that price; 2 TB costs $9, 4 TB costs $16, and 10 TB costs $38, which works out to **$3.80 per terabyte**. RamNode goes lower still at the bottom of the range, 160 GB of HDD with 2 TB of transfer for $4.

Two numbers decide almost every purchase in this category: dollars per terabyte of disk, and gigabytes of transfer included with it. The first falls as the disk grows. The second is where cheap plans quietly stop being comparable, because a fixed monthly quota, an unlimited-with-fair-use policy and bidirectional metering are three different products wearing the same label.

Here is the current price landscape, the $/TB arithmetic for plans people actually shortlist, the restore traffic that never shows up on a spec sheet, and where SpinServers' VPS line fits. Its plans are RAID-10 SSD with a 1 Gbps port and 4 to 20 TB of monthly transfer, with featured builds from $62/month. At $62 for 160 GB, it is not a cheap-disk purchase; it's a compute-and-bandwidth purchase, and the difference matters when you're comparing it against $5 HDD boxes.

> **Quick pick.** Cold backups or a media library under 2 TB: buy the biggest HDD plan you can afford per terabyte, and HostHatch's 2 TB at $9 is the easy reference point. Need SSD-backed I/O, a 1 Gbps port, IPv4 plus IPv6, and 4 to 10 TB of transfer on a machine that can also transcode or build: the SpinServers Application Server tiers are the ones to price out. 👉 [See SpinServers' current VPS configurations and cart prices](https://bit.ly/Spinservers)

## What SpinServers' VPS lineup actually contains

SpinServers splits its virtual servers into "Simple Application Servers" for websites and development work, plus larger Advanced and Hybrid KVM builds. Every configuration I could verify on the product page ships with a RAID-10 SSD system disk, a 1 Gbps network port, one IPv4 and one IPv6 address, and a monthly transfer allowance between 4 TB and 20 TB.

| Plan (as listed) | vCPU / RAM | Disk | Monthly transfer (port) | Price, USD/month | Order |
| --- | --- | --- | --- | --- | --- |
| Simple Application Server | 2 vCPU / 2 GB DDR4 | 40 GB RAID-10 SSD | 4 TB (1 Gbps) | Set at checkout | [See current price](https://bit.ly/Spinservers) |
| Simple Application Server | 6 vCPU / 8 GB DDR4 | 120 GB RAID-10 SSD | 8 TB (1 Gbps) | Set at checkout | [See current price](https://bit.ly/Spinservers) |
| Simple Application Server | 8 vCPU / 8 GB DDR4 | 160 GB RAID-10 SSD | 10 TB (1 Gbps) | Set at checkout | [See current price](https://bit.ly/Spinservers) |
| Simple Application Server | 12 vCPU / 12 GB DDR4 | 160 GB RAID-10 SSD | 10 TB (1 Gbps) | Starting from $62.00 | [See current price](https://bit.ly/Spinservers) |
| Hybrid KVM / Advanced Application Server | 32 vCPU / 32 GB | 500 GB SSD | 20 TB (1 Gbps) | Starting from $89.00 | [See current price](https://bit.ly/Spinservers) |

The product page publishes "starting from" figures only on the featured builds; the smaller tiers show their exact rate in the cart, so treat the cart as the source of truth rather than a review from months ago. Two other details belong in the same table because they change what the machine is useful for: port 25 is closed by default on every VPS, and opening it requires a support ticket with a justification, which they can refuse.

There is no spinning-disk storage tier in this lineup that I could verify. If your plan was to park 2 TB of cold data for under $10 a month, SpinServers is the wrong shop, and I'd rather say so before you spend $62. What the 12 vCPU build does give you for that money is 12 cores, 12 GB of RAM, 10 TB of transfer on a 1 Gbps port, and dual-stack IPs, which is a different product from a 160 GB disk with one core bolted to it.

Third-party write-ups of the dedicated-server side, published in early 2026, describe month-to-month billing with no setup fee, roughly 30-minute provisioning, free private networking between servers, and IPMI console access, with the hardware economics traced back to vertical integration with a used enterprise hardware trader in Texas. Those are third-party claims rather than product-page facts, but they explain the pricing pattern: you're buying last-generation enterprise gear at a discount, not new hyperscaler capacity.

## The $/TB arithmetic that decides which plan is "cheap"

Convert everything to dollars per terabyte per month, treating 1 TB as 1,000 GB so the numbers line up across providers. Then separate HDD from SSD, because they aren't competing for the same data.

| Plan | Disk | Monthly price | $/TB-month |
| --- | --- | --- | --- |
| HostHatch Storage 1TB | 1,000 GB | $5.00 | $5.00 |
| HostHatch Storage 4TB | 4,000 GB | $16.00 | $4.00 |
| HostHatch Storage 10TB | 10,000 GB | $38.00 | $3.80 |
| RamNode 650 GB | 650 GB | $12.00 | $18.46 |
| RamNode 4 TB | 4,000 GB | $64.00 | $16.00 |
| Contabo Storage VPS 10 (SSD) | 300 GB | $5.28 | $17.60 |
| Contabo Storage VPS 50 (SSD) | 1,400 GB | $35.60 | $25.43 |
| Synteq block storage | 1,000 GB | $4.00 | $4.00 |

HostHatch's curve is the steepest and the most useful: $5.00 per terabyte at 1 TB, $3.80 at 10 TB, a 24% drop for buying ten times the disk. RamNode sits higher per terabyte at every size, and the reason is visible in its spec sheet rather than its pricing. The 650 GB plan includes 8 TB of transfer and the 4 TB plan includes 150 TB, so part of what you pay goes into a bandwidth allowance HostHatch charges differently.

Contabo's SSD plans look expensive per terabyte ($17.60 at 300 GB, $25.43 at 1.4 TB) and the trend inside its own range is upward, not downward, because CPU and RAM grow faster than the disk does. You're buying a whole large VM with SSD storage attached, which is a sensible purchase for Nextcloud, container hosts and anything with random I/O. It's a poor purchase if all you want is somewhere to dump tarballs.

Synteq is the odd one in the table: flat $4 per TB per month, storage priced separately from compute, so a small VPS with a large volume doesn't force you into paying for cores you'll never use. Its volumes live on a distributed cluster and reattach to a healthy host if the physical machine fails, which is a real architectural difference from a single box with local drives.

One more ratio that almost nobody publishes: transfer per dollar. RamNode's 4 TB plan gives 150 TB of monthly transfer for $64, about $0.43 per TB of transfer. HostHatch's 10 TB plan gives 25 TB for $38, about $1.52. Neither figure appears in a comparison table, and either one can decide whether a seedbox or a restore-heavy backup target belongs on that host.

## Transfer is the second bill, and policies aren't interchangeable

Every plan above includes an allowance. What differs is the direction, the size, and the consequences of exceeding it.

- **HostHatch** publishes fixed GB quotas per plan: 2,500 GB on the 1 TB tier, 25,000 GB on the 10 TB tier. The storage page footnotes that bandwidth limits differ in the APAC region, so the same plan in a different location isn't the same product.
- **RamNode** also publishes fixed quotas, from 2 TB at the entry tier up to 150 TB on the 4 TB plan, with hourly rates listed alongside the monthly ones.
- **Contabo** separates directions: inbound is unlimited and unmetered, outbound is advertised as unlimited under a fair-use policy, and the terms reserve the right to throttle servers with exceptionally high or disruptive usage patterns.
- **Synteq** charges no egress fees at all, with a flat per-terabyte price that doesn't change when you read your data back.
- **DediRock**, according to a third-party write-up rather than its own page, counts inbound and outbound together, which halves the effective allowance.

Restores are where this becomes concrete. A backup you never touch costs nothing to keep; a backup you restore costs its full size in outbound transfer. Pull 2 TB back onto a machine with a 5,000 GB allowance and you've used 40% of the month in one afternoon. Run quarterly restore drills on a large dataset and the transfer line matters more than the disk price did. The same logic applies to media: a Plex library that streams a few hours a day moves far more data than the disk it sits on suggests, which is why a 150 TB allowance on a $64 plan can beat a $38 plan with a fifth of the bandwidth.

## Who should not buy a storage VPS

HDD capacity is built for sequential reads and writes: backups, media libraries, file sync, torrent clients, build artifacts, log archives. RamNode's own use-case list covers exactly that ground, and the third-party DediRock write-up is blunt that running a database on its spinning-disk nodes is painful. If your workload is random I/O, an HDD plan will disappoint you no matter how cheap the terabyte is.

The other mismatch is CPU. Entry tiers across this category give you one or two cores and 1 GB of RAM. Encrypted backup tools like WireGuard-backed Tailscale, plus compression, are CPU-bound, and a single core becomes the bottleneck long before the disk does. Media transcoding is worse: it will stall on a 1-core box even if the storage is generous.

If either of those describes you, a compute VPS with an NVMe root disk is the right shape. HostHatch's NVMe 2 GB starts at $4/month with 10 GB of NVMe and 1 TB of transfer, and that's a better home for a database than any 4 TB spinning disk. SpinServers' larger tiers fit the same category from the other direction: 8 to 32 vCPU on SSD RAID-10, with 8 to 20 TB of transfer and a full 1 Gbps port, which is what you need when the box has to serve or transcode, not just hold.

## Where the low monthly number comes from

Contabo's $5.28 is the most misquoted figure in this market. On its own page, that is the effective monthly rate for a 24-month subscription including applicable taxes, with a minimum initial contract of one month and a minimum following contract equal to the initial contract length. It is not a month-to-month rate, and treating it as one is how people end up surprised at renewal.

HostHatch and RamNode quote "from" prices that shift with location, and RamNode additionally publishes hourly rates, which tells you it expects short-lived deployments. DediRock's cheapest numbers come from annual promotional stock that sells out. SpinServers lists monthly starting prices on its featured builds, and the exact figure for the tier you want appears in the cart.

The pattern across all of them: the headline number is a first-term or best-case number. Long-run cost is that number multiplied by the term you actually signed, plus whatever overage your transfer profile produces.

## Which plan fits your workload

1. **Under 2 TB of cold data, price is the only variable.** HostHatch's 1 TB at $5 or 2 TB at $9. Take RamNode's 160 GB at $4 only if you also want the larger transfer allowance relative to disk.
2. **4 to 10 TB where transfer volume dominates.** RamNode's 4 TB at $64 with 150 TB of transfer beats capacity-focused plans once you're moving data constantly; HostHatch's 10 TB at $38 is the better buy if you're storing, not serving.
3. **SSD plus real CPU plus 1 Gbps plus 8 to 10 TB of transfer.** SpinServers' Application Server tiers, where the 12 vCPU / 12 GB build is the one with a published starting price. 👉 [Compare SpinServers' VPS tiers and monthly pricing](https://bit.ly/Spinservers)
4. **Storage that has to survive a host failure.** Distributed block storage (Synteq's model) over local disks on a single machine.
5. **No appetite for metering at all.** A flat per-terabyte price with no egress fees, or Contabo with the fair-use caveat understood up front.

Before you order, confirm four things: whether the price shown is monthly or the effective rate of a longer term; the transfer direction and quota; whether the disk is HDD or SSD; and how many IPv4 addresses are included, since RamNode includes one, SpinServers includes one IPv4 plus one IPv6, and Contabo includes both.

Get those four right and the "cheap" label stops being about the sticker. A $5 plan with 2 TB of egress and a $64 plan with 150 TB are answering different questions, and the only wrong answer is picking one for the other's job. 👉 [Price a SpinServers VPS against your shortlist](https://bit.ly/Spinservers)
