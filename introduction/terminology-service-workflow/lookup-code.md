# Lookup Code

This transaction allows a PoS, or any OHIE component, to access terminological ****information in the terminology service to retrieve detailed information on a code.  A typical example would be to retrieve descriptive information on a laboratory code from the LOINC Code System. 

Both external systems and systems inside the HIE may perform this transaction directly with the TS. The sequence diagram below shows the steps that occur for a system using this transaction.   

1. Lookup: Retrieve information on Code '26453-1' in the LOINC Code System.

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
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>The FHIR CodeSystem lookup operation: <a href="https://www.hl7.org/fhir/codesystem-operation-lookup.html">https://www.hl7.org/fhir/codesystem-operation-lookup.html</a>.
          HL7 FHIR Specifications v3.0 or higher support lookup. The response is
          an object that contains details about the code, including definition, status,
          designations, and properties.</p>
        <p>This workflow implements the IHE IT Infrastructure Technical Framework
          Supplement - Sharing Valuesets, Codes, and Maps (SVCM) Transaction: Lookup
          Code ITI-Y4.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The required CodeSystems have been preloaded into the Terminology Service
        and the specified code exists in the Code System.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system or other HIE component that is requesting
            to lookup a code.</li>
          <li>TS - Stores the curated official version of the terminology and codes
            for the health system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description 

The following is a description of the interaction steps. 

![](https://lh4.googleusercontent.com/IVUu_eE18fSlBI25iBniQ7y4DPM7qCbf8_30UqeFWSWl-DNM8FdYCzAIqRnBsMJMcogU1GbsA0VjBplO4eTX9cushkPFDEHoefAUp4vyMdHlqlnI2OT3rx7XFhl9FsZBXQ)

<table>
  <thead>
    <tr>
      <th style="text-align:left">Ref</th>
      <th style="text-align:left">Interaction</th>
      <th style="text-align:left">Data</th>
      <th style="text-align:left">Transaction Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Code Lookup request</td>
      <td style="text-align:left">
        <p>The validate-code request is triggered by a PoS or other HIE component.</p>
        <p>Input: A Concept Code and target Code System.</p>
      </td>
      <td style="text-align:left">FHIR CodeSystem Resource, $lookup operation</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Code Lookup response</td>
      <td style="text-align:left">
        <p>The response is sent back to the requesting system.</p>
        <p>Output: an object containing code information.</p>
      </td>
      <td style="text-align:left">FHIR CodeSystem Resource, $lookup operation</td>
    </tr>
  </tbody>
</table>

  


