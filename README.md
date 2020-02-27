# PhyNWInfo
## A Physical Network Information resource for reference networks
Reference Physical Network information JSON files, which can be used for various
Optical Network assessment 

## Introduction
For HeCSON and many other path calculation models, a detailed description of the
underlying physical network is needed.

More importantly, for QoT calculations, one needs information related to the
number of spans, the type of fiber used, the gain and noise figure of EDFAs on 
the links, etc. These files can be downloaded and used as a reference for 
various path calculation models or to reproduce the results of HeCSON.

## Networks
Currently, we have the following networks available
- Germany 50
- Norway
- Austria
- Nobel-EU

Each network is divided into its own directory and consists of the node, links
and demands json files. The nodes and the demand files are pretty straightforward.
However, the link json files consist of more information.

The basic nodes, links and demand files were taken from [SNDLib](http://sndlib.zib.de/home.action).

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

## A brief view on data generation methodology

The link information on the number of spans, span lengths, EDFA used and gain
calculated are generated from statistical observation of real core network deployments.

As an example, the Nobel-EU span distribution is seen as follows:

![Eu-Nobel Span Distribution](https://github.com/SaiPatri/PhyNWInfo/blob/master/spanlens-eu.png)

## More questions?

In case of doubts, or questions on how to use this dataset, please contact Sai Kireet Patri (SPatri@adva.com)
