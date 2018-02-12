# 2018-02-12 - Synthetic Evaluation

## Evaluation Description

To evaluate the effects of the automated error handling, a random error risk of 0.01 was configured on the RandomErrorComponent.

Additionally, to simulate that there is also a risk that the compensating action itself experiences a failure, a random error risk of 0.01 was added to the compensating action in the Collector component.

The system was executed using 100000 ingest submissions and observing the results gave the results below.

## Result Summary

| Result | Count |
| --- | ---:|
| IngestSuccessful | 99053 |
| CompensationSuccessful | 939 |
| CompensationFailed | 8 |

As can be seen in the table above, a total of 947 of the ingest submissions generated an error in the processing. This means that without automatic compensation of components with side effects, any component which has a side effect would have required manual work to handle 947 cases.

By allowing components to compensate for their actions in the case of failures during the ingest, the system was able to automatically handle 939 of these cases, leaving only 8 cases which need any kind of manual work.

## Ingest Events Generated During the Evaluation

A list of each ingest ID generated and its result classification can be found in [ingesteventclassifications.csv](ingesteventclassifications.csv).

All ingest event data generated can be found in the ZIP archive [ingestevents.zip](ingestevents.zip).

## A Note on Random Numbers

All random numbers generators in this evaluation are pseudo random generators, using the [.NET Random type](https://msdn.microsoft.com/en-us/library/system.random.aspx).