# Email-Eu-core – Virtual Community Analysis

This project was completed for **Laboratory 2: Visualization of Virtual Communities and Explanation of Results** for the Social Media Analytics course.

The objective of the laboratory is to detect, visualize, and interpret virtual communities in a real social network.

## Dataset

The project uses the **Email-Eu-core** dataset from the Stanford Large Network Dataset Collection (SNAP).

Dataset source:

https://snap.stanford.edu/data/email-Eu-core.html

The network represents email communication between members of a European research institution.

- **Node:** a member of the institution
- **Edge:** an email relationship between two members
- **Original network:** 1,005 nodes
- **Original edges:** 25,571 directed email relationships
- **Department labels:** available for all 1,005 nodes

The department labels are used to provide additional organizational context when interpreting the detected communities.

## Tools

The analysis was performed using:

- Python
- Pandas
- NetworkX
- NumPy
- Matplotlib
- Jupyter Notebook

## Community Detection

Communities were detected using the **Louvain algorithm**.

The original Email-Eu-core network is directed because email communication has a sender and a recipient. For community detection, the network was converted to an undirected graph so that the analysis focused on whether actors were connected rather than on the direction of individual email messages.

The resulting undirected network contains:

- **Nodes:** 1,005
- **Edges:** 16,706

The reduction from 25,571 to 16,706 edges occurs because reciprocal relationships between the same pair of actors are represented as a single undirected connection.

## Main Results

| **Measure** | **Result** |
| ------------------------- | ---------------- |
| Original nodes | 1,005 |
| Original directed edges | 25,571 |
| Undirected edges used for community detection | 16,706 |
| Detected communities | 28 |
| Community-level connections | 36 |

The Louvain algorithm identified **28 communities**. The communities vary considerably in size and are not completely isolated from one another.

The community-level analysis shows substantial interaction between several of the detected communities.

## Largest Communities

The largest detected communities are:

| **Community Size Ranking** | **Nodes** |
| -------------------------- | --------- |
| Rank 1 | 251 |
| Rank 2 | 145 |
| Rank 3 | 129 |
| Rank 4 | 129 |
| Rank 5 | 111 |
| Rank 6 | 93 |
| Rank 7 | 64 |
| Rank 8 | 54 |
| Rank 9 | 10 |

The analysis also identified **19 single-node communities**.

The largest community contains **251 nodes**, making it substantially larger than the other detected communities.

## Community Structure

The detected communities form an interconnected network rather than completely separated groups.

There are **36 connections between the 28 detected communities**.

Some of the strongest community-level connections are:

| **Community Pair** | **Network Connections** |
| ------------------ | ----------------------- |
| Community 8 – Community 28 | 815 |
| Community 2 – Community 8 | 801 |
| Community 3 – Community 8 | 725 |
| Community 1 – Community 8 | 556 |
| Community 6 – Community 8 | 490 |

Community 8 is particularly well connected to several other communities and occupies an important position in the community-level network.

Community size and connectivity differences are visible in the analysis. However, community density was not calculated separately, so no direct claim is made about which community is the densest.

## Important Actors

Important actors were examined using **degree centrality** and **betweenness centrality**.

**Node 160** was particularly prominent:

- **Degree:** 347
- **Betweenness centrality:** 0.087415
- **Community:** 6
- **Connected to:** 9 detected communities

Node 160 had both the highest degree and the highest betweenness centrality among the analyzed nodes.

Other highly connected actors include:

- Node 121 — degree 234
- Node 82 — degree 233
- Node 107 — degree 221
- Node 86 — degree 218

Several actors were found to have connections spanning **9 different communities**, indicating that they can occupy important cross-community positions.

## Community Type

The Email-Eu-core network most closely resembles an **in-group community structure**.

The network represents communication between members of the same research institution, and the detected communities consist of groups of actors with stronger patterns of interaction within the network.

The department analysis provides additional support for this interpretation. Some communities are strongly associated with particular departments, while other communities contain members from several departments.

However, the network is not a perfectly separated in-group structure because several communities have substantial connections with one another.

## Community Meaning

The department labels provide additional information for interpreting the detected communities.

Some communities show strong department concentration:

- **Community 4:** 88 of 93 members belong to Department 14 (**94.62%**)
- **Community 3:** 93 of 129 members belong to Department 4 (**72.09%**)
- **Community 1:** 43 of 64 members belong to Department 1 (**67.19%**)

In contrast, the largest community, **Community 8**, contains 251 nodes, but its largest department group contains only 47 members (**18.73%**).

This suggests that some communities may correspond closely to organizational departments or groups of closely interacting colleagues, while others reflect communication patterns that cross department boundaries.

The network shows patterns of interaction, but it does not establish why the communities exist or what was discussed in the emails.

## Connections Between Communities

The community-level analysis shows that communication occurs between the detected groups.

The strongest observed connection is between **Community 8 and Community 28**, with **815 network connections**.

Community 8 also has strong connections with Communities 2 and 3, with **801** and **725** connections respectively.

Several actors have connections spanning **9 different communities**. Node 160 is particularly notable because it has the highest degree, the highest betweenness centrality, and connections to 9 communities.

These cross-community connections indicate potential interaction and information flow between the detected groups. However, the network alone cannot establish what information was exchanged or why actors communicated across communities.

## Visualization

The project includes several network visualizations.

The full network visualization shows all detected communities and their structural relationships.

A second visualization focuses on the **nine main communities containing at least ten nodes**, making the major community structure easier to observe.

The community-level visualization represents each detected community as a node:

- Larger nodes represent larger communities.
- Different colors distinguish communities.
- Thicker edges represent stronger connections between communities.

## Limitations

The analysis has several limitations.

- An email relationship does not necessarily indicate the strength or nature of a social relationship.
- Louvain communities are based on network structure and should not automatically be interpreted as formal organizational departments.
- The full network contains 1,005 nodes, making some individual relationships difficult to observe visually.
- Community density was not calculated separately.
- The network structure does not establish why particular communities or communication patterns exist.
- The content of the emails was not analyzed, so the analysis cannot determine what information was exchanged.

## Project Structure

```text
├── Social_Media_Analytics_Lab2.ipynb
├── README.md
├── report/
│   └── Social_Media_Analytics_Lab2_Report_.pdf
└── data/
    ├── email-Eu-core.txt
    └── email-Eu-core-department-labels.txt
