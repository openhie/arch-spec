# OpenHIE Shared Health Record \(SHR\)

The Shared Health Record \(SHR\) facilitates the sharing of clinical information between health information systems to enable better patient care, thus improving health outcomes.  The Shared Health Record is a means of allowing different services to share health data stored in a centralized data repository.  It contains a subset of normalized data for a patient from various systems such as an electronic medical record or the Laboratory Information Management System. This record is queried and updated between the different institutions and systems that are authorized to do so.  The Shared Health Record is distinct from a data warehouse; it is an operational, real-time transactional data source.

A shared health record is normalised if all metadata items such as patient, provider, and facility identifiers are resolved to appropriate universal identifiers \(as opposed to their local identifiers as used by a client system\). In addition, all terminology codes in use need to be mapped to an appropriate reference terminology to ensure that the information is consistently understood.

See also [Non-Functional Requirements](non-functional-requirements.md). 

## **OpenHIE SHR Workflow Requirements** 

A [core principle of the OpenHIE architecture](https://wiki.ohie.org/display/resources/Architectural+Principals) is to allow the various infrastructure services \(such as the SHR\) to be interchangeable. To support this, the [OpenHIE Standards and Profiles](https://wiki.ohie.org/display/documents/OpenHIE+Standards+and+Profiles) used by the Shared Health Record are outlined in the workflows below.  

To be an OHIE SHR component, the SHR application must be able to support the OHIE workflows listed below.  Implementations may support only the workflows needed to support their use case:

| **\#** | **SHR Workflows \(Described in detail in the later part of this document\)** | **Recommendation/ Requirement** |
| :--- | :--- | :--- |
| \*\*\*\*[**SHRWF-1**](../introduction/shared-health-record/save-patient-level-clinical-data-workflow.md)\*\*\*\* | [Save patient-level clinical data workflow](../introduction/shared-health-record/save-patient-level-clinical-data-workflow.md) | Requirement |
| \*\*\*\*[**SHRWF-2**](../introduction/shared-health-record/query-patient-level-clinical-data-workflow.md)\*\*\*\* | [Query patient-level clinical data workflow](../introduction/shared-health-record/query-patient-level-clinical-data-workflow.md) | Requirement |

## **OpenHIE SHR Functional Requirements**

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left"><b>SHR Functional Requirement</b>
      </th>
      <th style="text-align:left"><b>Recommendation/ Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>SHRF-1</b>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Stores patient level clinical data that forms a patient&#x2019;s electronic
          health record</p>
        <p><b>a. </b>Stores unstructured clinical data such as PDFs and narrative
          text</p>
        <p><b>b.</b> Stores structured clinical data such as an encounter with several
          discrete observations, compatible with a standard exchange format</p>
        <p><b>c. </b>Relating clinical information to other clinical information,
          e.g., annotating/describing a document with discrete observations</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-2</b>
      </td>
      <td style="text-align:left">Expose services that have the ability to receive and save patient clinical
        data in unstructured form, both text or binary (PDF/image), annotated with
        sufficient metadata to identify patient/provider.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-3</b>
      </td>
      <td style="text-align:left">Expose services that have the ability to receive and save patient clinical
        data in a structured form such as CDA documents or FHIR resources.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-4</b>
      </td>
      <td style="text-align:left">Expose services that have the ability to receive and save patient clinical
        data In a form that contains both structured and unstructured elements.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-5</b>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>Exposes services that respond to queries for a patient&#x2019;s EHR</p>
        <p><b>a.</b> Can return a specific known document or a list of documents for
          a patient (as it was submitted)</p>
        <p><b>b.</b> Can return a list of discrete observations for a patient that
          satisfy specific query parameters. This data can subsequently be used for
          trending or providing the previous encounters that a patient has had.</p>
        <p><b>c.</b> Can return a full set of clinical information stored about a
          patient</p>
        <p><b>d. </b>Return patient summary - everything the SHR knows about a patient
          with links to fetch the individual data items</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-6</b>
      </td>
      <td style="text-align:left">The SHR shall maintain the context in which the data was submitted.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-7</b>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>The SHR should keep detailed audit logs of all interactions with clinical
          data</p>
        <p><b>a.</b> Keep audit logs of any clinical and demographic data that is
          stored or changed. Logging who has accessed/viewed clinical information
          does NOT need to be stored, this is something that an interoperability
          layer could log.</p>
        <p><b>b.</b> Records and versions updates; records can never be deleted, only
          marked as such; any previous update should not rewrite old data; no information
          should ever be removed from the system.</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-8</b>
      </td>
      <td style="text-align:left">The SHR should support the ability to export data for secondary use.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-9</b>
      </td>
      <td style="text-align:left">The SHR should provides interfaces/extension points at various stages
        of the data lifecycle to allow for semantic validation or simple decision
        support.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-10</b>
      </td>
      <td style="text-align:left">The SHR should allow for storage and retrieval of basic privacy/policy
        constraints (access control-restrict part of record and restrict entire
        record).</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-11</b>
      </td>
      <td style="text-align:left">The SHR should be able to store identified and predefined observational
        data mapped to standard reference terminology.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SHRF-12</b>
      </td>
      <td style="text-align:left">The SHR should have a mechanism to resolve conflicts if records are submitted
        simultaneously.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
  </tbody>
</table>

