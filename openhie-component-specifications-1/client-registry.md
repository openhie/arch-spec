# Client Registry \(CR\)

The identity of an individual who receives health services is crucial to enabling health care record sharing across institutions and systems. Yet, sharing health care records can be a challenge in a complex environment where there are multiple systems across multiple health care institutions and each institution and/or system has a different way to identify their clients. Even in environments where citizens are assigned national identification cards, there is a need to ensure the unique identity of an individual among the myriad fragmented information systems that collectively represent a person’s electronic health record. The Client Registry is designed to assist in uniquely identifying individuals who receive health care services by:

* Maintaining a central registry of all patients and their demographics and assigning a unique identifier to each patient. 
* Linking patient registration entries that result due to changes in patient demographics \(patient moved to another location\), data entry errors during patient registration, or missing demographic information.
* Enabling health care workers to identify facilities at which a patient has received care.

See also [Non-Functional Requirements](non-functional-requirements.md).

## OpenHIE CR Workflow Requirements

A [core principle of the OpenHIE architecture](https://wiki.ohie.org/display/resources/Architectural+Principals) is to allow the various infrastructure services \(such as the CR\) to be interchangeable. To support this, the [OpenHIE Standards and Profiles](https://wiki.ohie.org/display/documents/OpenHIE+Standards+and+Profiles) used by the Client Registry are outlined in the workflows below. To be an OHIE CR component, the CR application must be able to support the OHIE workflows listed below. Implementations may support only the workflows needed to support their use case:

|  \# | **CR Workflows \(Described in detail in the later part of this document\)** | Recommendation/Requirement |
| :--- | :--- | :--- |
| **CRWF-1** | A CR shall support the “[Create patient demographic record workflow](../introduction/patient-identity-management-workflows/create-patient-demographic-record-workflow-1.md)” | Requirement |
| **CRWF-2** | A CR shall support the “[Update patient demographic record workflow](../introduction/patient-identity-management-workflows/update-patient-demographic-record-workflow.md)” | Requirement |
| **CRWF-3** | A CR shall support the “[Query patient demographic records by identifier workflow](../introduction/patient-identity-management-workflows/query-patient-demographic-records-by-identifier-workflow.md)” | Requirement |
| **CRWF-4** | A CR shall support the “[Query patient demographic records by demographics workflow](../introduction/patient-identity-management-workflows/create-patient-demographic-record-workflow.md)” | Requirement |

## OpenHIE CR Functional Requirements

The following are typical features of a client registry, or master patient index. Depending upon the desired use case\(s\), the system may support many or all of these functional features.

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left"><b>CR Functional Requirement</b>
      </th>
      <th style="text-align:left"><b>Recommendation/ Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>CRF-1</b>
      </td>
      <td style="text-align:left">
        <p>The system should support configurable entity matching, a service to assist
          in identifying duplicate patients.</p>
        <p><b>a.</b> The rules for determining whether two records match each other
          should be configurable (e.g., ability to use both statistical and/or rules
          based, etc.).</p>
        <p><b>b.</b> The blocking strategy for loading potential matches before the
          matching rules are applied should be configurable.</p>
        <p><b>c.</b> Any configurable component should have an interface so that advanced
          users can write their own implementation from scratch if desired.</p>
        <p><b>d.</b> Any interface should have at least one default implementation.</p>
        <p><b>e.</b> The default implementation should be flexible and configurable
          so that non-programmers can adjust it to meet their needs.</p>
        <p><b>f.</b> To the extent possible, CR system configuration information should
          be managed using consistent and easy to access methods, such as a database,
          properties files, or XML files).</p>
        <p><b>g.</b> It should allow &#x201C;wizard-based&#x201D; or &#x201C;guided&#x201D;
          setup of matching rules.</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-2</b>
      </td>
      <td style="text-align:left">
        <p>The system shall support patient linking and de-duplication.</p>
        <p><b>a.</b> The system shall implement accurate and efficient patient linking
          and de-duplication methods.</p>
        <p><b>b.</b> It shall provide an easy to use and intuitive way to see merge/linkage
          operations,</p>
        <p><b>c.</b> It should allow an easy to use and intuitive way of manually
          accepting or rejecting merge suggestions, with the ability to choose fields
          from either record to be merged.</p>
      </td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-3</b>
      </td>
      <td style="text-align:left">
        <p>The system should support the ability to track and monitor inbound/outbound
          transactions.</p>
        <p><b>a.</b> The system must have the capacity to record receipt and transmission
          of transactions.</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-4</b>
      </td>
      <td style="text-align:left">The system should support synchronization of client IDs with a Shared
        Health Record (SHR).</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-5</b>
      </td>
      <td style="text-align:left">The system should support a UI to review and manually adjudicate uncertain
        (&#x201C;potential&#x201D;) matches, and override incorrect matches.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-6</b>
      </td>
      <td style="text-align:left">
        <p>The system should support configurable attributes including:</p>
        <p><b>a.</b> The attributes that form a patient record and are used for matching
          should be configurable.</p>
        <p><b>b.</b> The implementation can include an example/default patient schema.</p>
        <p><b>c.</b> It should be easy to add attributes to the schema.</p>
        <p><b>d.</b> It should also be easy to remove attributes from the default
          model (or start over from scratch).</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-7</b>
      </td>
      <td style="text-align:left">
        <p>The system should support error management</p>
        <p><b>a.</b> Ensure that error handling comprehensively captures and logs
          all related exceptions, and to the extent possible, shows relationships
          between exceptions.</p>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-8</b>
      </td>
      <td style="text-align:left">The system shall manage a full audit log of changes to data as well as
        configurations as well as users.</td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-9</b>
      </td>
      <td style="text-align:left">Privacy/Security: The system should have functions including user management
        and access controls.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>CRF-10</b>
      </td>
      <td style="text-align:left">The system should be able to persist the parent/child relationship, birth
        order, and multi-birth indicator.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
  </tbody>
</table>

