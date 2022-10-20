# PhyNWInfo
## [UPDATE: For OFC 2023 submission metadata, please refer to OFC2023 folder]

## A Physical Network Information resource for reference networks
Reference Physical Network information JSON files, which can be used for various
Optical Network assessment 

## Introduction
For flexible grid optical network planning, a detailed description of the
underlying physical network is needed.

More importantly, for QoT calculations, one needs information related to the
number of spans, the type of fiber used, the gain and noise figure of EDFAs on 
the links, etc. 

For generating traffic demands, we use a traffic model described in the paper [Planning Optical Networks for Unexpected Traffic Growth](https://arxiv.org/abs/2012.04360).


These files can be downloaded and used as a reference for various path calculation models or to reproduce the results of our published works, like [HeCSON: OFC 2020](https://arxiv.org/abs/2005.07610), [multi-period planner: ECOC 2020](https://arxiv.org/abs/2012.04360), or [Dynamic Network Reconfigurations: Accepted for OFC 2021](https://mediatum.ub.tum.de/doc/1601724/2y5lg1p2idvmvj7rrpja9fz31.Optical_Rerouting_OFC.pdf).

## Networks
Currently, we have the following networks available
- Germany 50
- Norway
- Germany 17
- Nobel-EU
- US Abilene
- Spain
- Sweden

Each network is divided into its own directory and consists of the node, links
and demands json files.

The basic nodes, links and demand files were taken from [SNDLib](http://sndlib.zib.de/home.action) and further modified to suit optical networks.
The Spanish and Swedish topologies can be found in [Internet Topology Zoo](http://www.topology-zoo.org/dataset.html) as RedIRIS and OptoSUNET topologies respectively.

## Physical Node information
Traverse to the node information file. Each node consists the following details.
"NodeID": \[ Node_Name, cood-y, cood-x, num_of_IXPs, num_of-DCs \]
IXPs - Internet Exchange Points and DCs - Data centers (taken from [Data-center map](https://www.datacentermap.com/) )
Eg:
"0": [
        "Berlin",
        506.0,
        955.0,
        7,
        16
 ]
 

## Physical Link Information

Each link is numbered and has the following properties:
- Link No.
- Start node 
- End Node
- Distance (km)
- Number of placed Channels
- number of spans
- Span List

The span list contains a list of spans for each of the links and these properties
are:
- SpanName
- FiberType
- SpanLength (km)
- EDFA Gain (dB)
- attn (dB/km)

An example is as follows:
```
"4": {
        "linkNo": 4,
        "startNode": "Aachen",
        "endNode": "Koeln",
        "linkDist": 94.41,
        "noChannels": 0,
        "noSpans": 2,
        "spanList": [
            {
                "LinkName": "Span_Aachen_Koeln_1",
                "FiberType": "G.652",
                "SpanLength": 92,
                "EDFAGain": 20.24,
                "attnDB": 0.22
            },
            {
                "LinkName": "Span_Aachen_Koeln_2",
                "FiberType": "G.652",
                "SpanLength": 2.4,
                "EDFAGain": 0.53,
                "attnDB": 0.22
            }
        ]
    }
```
## A brief view on data generation methodology

The link information on the number of spans, span lengths, EDFA used and gain
calculated are generated from statistical observation of real core network deployments.

As an example, the Nobel-EU span distribution is seen as follows:

![Eu-Nobel Span Distribution](https://github.com/SaiPatri/PhyNWInfo/blob/master/Inkedspanlens-eu_LI.jpg)

## Traffic Growth
Traffic growth occurs non-homogeneously, according to a novel traffic model. Once published in an academic publication, this will be included in the repository. The graphs from our previous publications are available in the folder Traffic Model. The traffic growth depends on the node-importance metric. Here shown is an example of the node size according to their importance in the Nobel-Germany network.
![Nobel-Germany Node Importance](https://github.com/SaiPatri/PhyNWInfo/blob/master/germany_node_traffics.PNG)


## More questions?

In case of questions on how to use this dataset, or opportunities for extension/collaboration please contact Sai Kireet Patri (SPatri@adva.com).

## How to Cite:
@misc{phynwinfo,
    title= {Github, \textit{Physical Network Information}},
    howpublished= "\url{www.github.com/SaiPatri/PhyNWInfo}, Accessed: yyyy-mm-dd",
    authors={Patri, Sai Kireet},
}
