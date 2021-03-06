# Query Code Systems

This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service to query for Code Systems.  A typical example would be to request the set of Code Systems defined by HL7.

Both external systems and systems inside the HIE may perform this transaction directly with the TS. The sequence diagram below shows the steps that occur for a system using this transaction.   

1. Query Code Systems: What Code Systems have a publisher name that contains 'HL7'?

<table>
  <thead>
    <tr>
      <th style="text-align:left">Workflow Maturity</th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/Vp6XBRGu-U_Dmd5EKNpCZvEEum0CxOcHOj9NgHh8UMMNLMlXHmLcUE_YWueDRr4uqWLzpPfzSBLJ2k33XQIelLypjQ4wyrD17-t33GtLa8fFxW9AYDvXhiJmBl4VaLgKDg"
          alt/>
        </p>
        <p><b>    Mature</b>
        </p>
      </th>
      <th style="text-align:left">
        <p></p>
        <ul>
          <li><b>One or more OpenHIE implementations of this workflow exist  in one or more countries</b>
          </li>
          <li><b>Workflow is defined and ARB approved</b>
          </li>
          <li><b>Workflow is supported by mature standards</b>
          </li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>The FHIR Code Systems and supported search parameters are defined in:
          <a
          href="https://www.hl7.org/fhir/valueset.html">https://www.hl7.org/fhir/codesystem.html</a>. Searching in FHIR is described
            in <a href="https://www.hl7.org/fhir/search.html">https://www.hl7.org/fhir/search.html</a>.
            HL7 FHIR Specifications v3.0 or higher support Code Systems. The response
            is a Bundle of CodeSystem Resources satisfying the search parameters.</p>
        <p>This workflow implements the IHE IT Infrastructure Technical Framework
          Supplement - Sharing Valuesets, Codes, and Maps (SVCM) Transaction: Query
          Code System ITI-Y2.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The required Code Systems have been preloaded into the Terminology Service.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system or other HIE component that is that
            is querying for Code Systems.</li>
          <li>TS - Stores the curated, official version of the Code Systems for the
            health system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description 

The following is a description of the interaction steps. 

![](https://lh5.googleusercontent.com/vzHUYYmxsJZAdYAIakuwvSwmpi3I1LFC_hGCGOLbCHTMt8mUETcrhI5J49tEhzt73QN2SOpEDafDoNjVHS8vNw7VLhnLpthIsxCMWjLMmXqAgF7JPo5j5o26EmRQsHdfiQ)

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left">Interaction</th>
      <th style="text-align:left">Data</th>
      <th style="text-align:left">Transaction Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Query Code System request</td>
      <td style="text-align:left">
        <p>The Code System search request is triggered by a PoS or other HIE component.</p>
        <p>Input: A set of FHIR search parameters.</p>
      </td>
      <td style="text-align:left">FHIR CodeSystem Resource</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Query Code System request</td>
      <td style="text-align:left">
        <p>The response is sent back to the requesting system.</p>
        <p>Output: a Bundle of CodeSystem Resources that satisfy the search parameters.</p>
      </td>
      <td style="text-align:left">FHIR CodeSystem Resource</td>
    </tr>
  </tbody>
</table>

## 

