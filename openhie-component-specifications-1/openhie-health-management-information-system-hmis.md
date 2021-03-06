# OpenHIE Health Management Information System  \(HMIS\)

A Health Management Information System \(HMIS\), also called a Routine Health Information System, facilitates the collection of periodic health service delivery and public health indicators from a variety of information systems and the effective use of information at facility, district, and higher levels to help improve health care outcomes.

See also [Non-Functional Requirements](non-functional-requirements.md). 

## **OpenHIE HMIS Workflow Requirements** 

The following workflow is currently supported, and an FHIR-based message is emerging. 

| \# | **HMIS Workflows \(Described in detail in the later part of this document\)** | **Recommendation / Requirement** |
| :--- | :--- | :--- |
| \*\*\*\*[**HMISWF-1**](../introduction/aggregate-reporting-workflows/validate-and-save-aggregate-data.md)\*\*\*\* | [Validate and Save Aggregate Data](../introduction/aggregate-reporting-workflows/validate-and-save-aggregate-data.md) | Required |

## **OpenHIE HMIS Functional Requirements** 

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left"><b>HMIS Functional Requirements</b>
      </th>
      <th style="text-align:left"><b>Recommendation / Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>HMISF-1</b>
      </td>
      <td style="text-align:left">An HMIS shall act as a datastore for integrated health system data which
        can be used for better decision making in the health system.</td>
      <td style="text-align:left">Required</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>HMISF-2</b>
      </td>
      <td style="text-align:left">An HMIS should provide mechanisms (preferably web based) for data entry.</td>
      <td
      style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>HMISF-3</b>
      </td>
      <td style="text-align:left">An HMIS should provide mechanisms to improve the quality and validity
        of data (smart forms, validation rules, etc.).</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>HMISF-4</b>
      </td>
      <td style="text-align:left">An HMIS should provide standard interfaces for the importing of data from
        other systems (e.g., ADX, FHIR).</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>HMISF-5</b>
      </td>
      <td style="text-align:left">An HMIS should support the use of an accurate list of health facilities
        and their geographic and administrative distribution.</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>HMISF-6</b>
      </td>
      <td style="text-align:left">An HMIS should provide interfaces for sharing health facility information
        with other systems (facility registry).</td>
      <td style="text-align:left">Recommended</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>HMISF-7</b>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>To support its primary function of data use, an HMIS should:</p>
        <ul>
          <li>Be able to further aggregate and analyze data (e.g., provide annual report
            from monthly data)</li>
          <li>An HMIS should offer an interface to query its data in a flexible way
            across different dimensions (analytics API)</li>
          <li>An HMIS should provide customized graphic visualizations of data</li>
        </ul>
      </td>
      <td style="text-align:left">Recommended</td>
    </tr>
  </tbody>
</table>

