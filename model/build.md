SPDX-License-Identifier: Community-Spec-1.0

# Build

## Summary

Class that describes a build of software/artifacts.

## Description

A build is a representation of the process in which a piece of software or
artifact is built. It encapsulates information related to a build process and
provides an element from which relationships can be created to relate the build
to the inputs/outputs, and entities related to the build (e.g. builders,
identities, etc.).

Definitions of "BuildType", "ConfigSource", "Parameters" and "Environment" follow
those defined in [SLSA provenance](https://slsa.dev/provenance/v0.2).

ExternalReferences:
- buildInvocationId
- logReference
- logFile

<!-- 

At the moment, logs wil be refered to via logReference and logFile via external references,
and if/when external references become referencable SPDX elements, we can create the relationship
"LOG_TO" to link them together.

-->

## Metadata

- name: Build
- SubclassOf: Core:Element
- Instantiability: Concrete

## Properties

- buildType
  - type: anyURI
  - minCount: 1
  - maxCount: 1
- configSourceEntrypoint
  - type: string
  - minCount: 0
- configSourceUri
  - type: string
  - minCount: 0
- configSourceDigest
  - type: xsd:string
  - minCount: 0
- parameters
  - type: map<string>string
  - minCount: 0
- startTime
  - type: xsd:DateTime
  - minCount:0
  - maxCount:1
- endTime
  - type: xsd:DateTime
  - minCount:0
  - maxCount:1
- environment
  - type: xsd:map<string>string
  - minCount: 0
