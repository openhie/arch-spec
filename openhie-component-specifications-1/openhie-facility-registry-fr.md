# OpenHIE Facility Registry \(FR\)

The purpose of a health facility registry is to act as the central authority to collect, store, and distribute an up to date and standardized set of facility data.  The resulting standardized and current facility dataset stored in the registry is called the Master Facility List \(MFL\).  While these concepts are closely related, a facility registry can be understood as the technology that manages and shares facility data and an MFL is the standardized data stored in the tool. 

See also [Non-Functional Requirements](non-functional-requirements.md). 

## **OpenHIE FR Workflow Requirements** 

| \# | **FR Workflows \(Described in detail in the later part of this document\)** | **Recommendation/ Requirement** |
| :--- | :--- | :--- |
| \*\*\*\*[**FRWF-1**](../introduction/care-services-discovery/query-health-worker-and-or-facility-records-workflow.md)\*\*\*\* |  [Query health worker and/or facility records workflow.](../introduction/care-services-discovery/query-health-worker-and-or-facility-records-workflow.md) | Required |

## OpenHIE FR Functional Requirements 

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>#</b>
      </th>
      <th style="text-align:left"><b>FR Functional Requirement</b>
      </th>
      <th style="text-align:left"><b>Recommendation/ Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>FRF-1</b>
      </td>
      <td style="text-align:left">The system shall support the ability to create, define, and evolve the
        attributes &amp; associated data dictionary for a registry.</td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-2</b>
      </td>
      <td style="text-align:left">The system shall support the ability to create, define, and maintain multi-organizational
        hierarchies of facilities and related geo-objects.</td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-3</b>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>A system should support the collection of data for the following minimum
          facility attributes dataset: (<a href="https://www.who.int/healthinfo/MFL_Resource_Package_Jan2018.pdf?ua=1">Refer to WHO, USAID MFL resource package - Guidelines for countries</a>)</p>
        <p><b>Signature Domain</b>
        </p>
        <ul>
          <li>Facility name</li>
          <li>Facility type (e.g., hospital, clinic, mobile clinic, lab, pharmacy)</li>
          <li>Facility ownership/managing authority</li>
          <li>Facility physical address</li>
          <li>Facility contact information</li>
          <li>Record date</li>
          <li>Operational status</li>
          <li>Administrative level/areas</li>
          <li>Geographic coordinates</li>
          <li>Facility unique identifier</li>
        </ul>
        <p><b>Service domain</b>
        </p>
        <ul>
          <li>Type of Services offered - Lab, HIV, TB, etc.</li>
          <li>Human resource for health, numbers by cadre</li>
          <li>Opening and closing times</li>
          <li>Common and Mapped Identifiers per Location</li>
          <li>Details on Infrastructure - Power, Water, etc.</li>
        </ul>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-4</b>
      </td>
      <td style="text-align:left">The system shall support the ability to set up and manage users, permissions
        for reading data, writing data (posting, validation, publishing), viewing
        data and system administration.</td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-5</b>
      </td>
      <td style="text-align:left">At minimum an FR should support the ability to create roles and assign
        permissions to the roles. Example roles would be the Master Administrator,
        Data curator, Health Officer.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-6</b>
      </td>
      <td style="text-align:left">The system should have flexible standards-based APIs, preferably RESTful
        API.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-7</b>
      </td>
      <td style="text-align:left">The system should have the ability to pull and/or push data to other systems
        (.csv) based on defined criteria.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-8</b>
      </td>
      <td style="text-align:left">The system shall support the ability to do bulk imports.</td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-9</b>
      </td>
      <td style="text-align:left">The system should support the ability to search for facilities by attribute.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-10</b>
      </td>
      <td style="text-align:left">The system should support the ability to see the facility located on a
        map.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-11</b>
      </td>
      <td style="text-align:left">The system should allow public access to view data that is relevant to
        the public (e.g. services provided by a facility)</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FRF-12</b>
      </td>
      <td style="text-align:left">The system should support facility data curation to manage site status
        changes (closures, openings, service changes)</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FR-13</b>
      </td>
      <td style="text-align:left">The system should generate standard and customizable reports inline with
        the core FR attributes.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>FR-14</b>
      </td>
      <td style="text-align:left">The facility registry should align with the primary Master Facility List
        at minimum, or influence its update.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
  </tbody>
</table>

