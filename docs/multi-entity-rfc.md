# Multi Entity Anomaly Detection RFC

The purpose of this request for comments (RFC) is to introduce our plan to enhance Anamaly Detection for OpenDistro with the support of multiple entity. This RFC is meant to cover the high level functionality of the multi entity support and doesn’t go into implementation details and architecture.

## Problem Statement

Currently the Anomaly Detection for Elasticsearch for OpenDistro only support single entity use case. (e.g. average of cpu usage across all hosts, instead of cpu usage of individual hosts). For multi entity cases, users have to manually create individual detectors for each entity, which is time consuming, and becomes infeasible when there are hundreds or thousands of entities.

## Proposed solution

We propose to create a new type of detector to support multi entity use case. With this feature, users only need to create one single detector to cover all entities that can be categorized by one or multiple fields. They will also be able to view the results of the anomaly detection in one unified report.

### Create Detector

Most of the detector creation workflow is similar to the single entity detectors, the only additional input is a categorical field, e.g. ip_address, which will be used to split data into multiple entities. We’ll start with supporting only one categorical fields. We’ll add support of multiple categorical fields in future releases.

### Anomaly Report

The output of multi entity detector will be categorized based on entities. The entities with most anomaly detected will be presented first in a heatmap plot. Users also have the option to click into each entity for more details about the anomalies. 

### Entity capacity

Supporting multiple entities takes extra resource, especially memory. The total number of allowed entities depends on the cluster configuration, but in general we are planning to support up to 10K entities in the initial release. 

## Providing Feedback

If you have comments or feedback on our plans for Multi Entity support for Anomaly Detection, please comment on the [original GitHub issue](https://github.com/opendistro-for-elasticsearch/anomaly-detection/issues/xxx) in this project to discuss.
