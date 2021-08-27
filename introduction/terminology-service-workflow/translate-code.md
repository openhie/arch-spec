# Translate Code

 ****This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service and retrieve the translation, or "mapping" of a Concept in one Code System to a Concept in another Code System. Mapping is frequently required when patient data is collected using Concepts/Codes from one Code System but the data must be reported or aggregated, say for decision support, in a different Code System. The set of such associated Concepts, usually for a specific use-case, are stored in the Terminology Service in a FHIR Resource called a ConceptMap.

Both external systems and systems inside the HIE may perform this transaction directly with the TS.  The sequence diagram below shows the steps that occur for a system using this transaction.

1. Mapping: Using the ConceptMap 'ICD-10 to SNOMED CT Diseases', retrieve the SNOMED CT Concept Code\(s\) that is associated with '123XYZ' in ICD-10.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Workflow Maturity</th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/Vp6XBRGu-U_Dmd5EKNpCZvEEum0CxOcHOj9NgHh8UMMNLMlXHmLcUE_YWueDRr4uqWLzpPfzSBLJ2k33XQIelLypjQ4wyrD17-t33GtLa8fFxW9AYDvXhiJmBl4VaLgKDg"
          alt/>
        </p>
        <p><b>   Mature</b>
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
        <p>The FHIR ConceptMap translate operation: <a href="http://build.fhir.org/conceptmap-operation-translate.html">http://build.fhir.org/conceptmap-operation-translate.html</a>.
          HL7 FHIR Specifications v3.0 or higher support translate. The response
          is a set of FHIR Parameter objects that include a &apos;result&apos; (whether
          there is an acceptable match) and a list of possible matches. The list
          of matches may include notes of Codes for which mappings are specifically
          excluded, and qualifications on the applicability of matches.</p>
        <p>This workflow implements the IHE IT Infrastructure Technical Framework
          Supplement - Sharing Valuesets, Codes, and Maps (SVCM) Transaction: Translate
          Code ITI-Y7.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The required ConceptMap and associated CodeSystem(s) have been preloaded
        into the Terminology Service.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system or other HIE component that is requesting
            the translation.</li>
          <li>TS - Stores the curated, official version of the ConceptMap for the health
            system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description**

The following is a description of the interaction steps. 

![](https://lh3.googleusercontent.com/EthDly9fk9f2CNixr1QkJS3-iufEkWRZmH_4K0p0yYETwD4OukltPQ0-gxiblSB-Oz-jsJvEAcAfljVxWhQUmShBpwDnKwsi_sEoAEbFn64xobObbBf2jU9C5moGvxvjZA)

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
      <td style="text-align:left">ConceptMap translate request</td>
      <td style="text-align:left">
        <p>The translate request is triggered by a PoS or other HIE component.</p>
        <p>Input: The ConceptMap name and source Code and CodeSystem.</p>
      </td>
      <td style="text-align:left">FHIR ConceptMap Resource, $translate operation</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">ConceptMap translate response</td>
      <td style="text-align:left">
        <p>The response is sent back to the requesting system.</p>
        <p>Output: a set of parameters including a Boolean &apos;result, and a list
          of, possibly qualified, Code matches.</p>
      </td>
      <td style="text-align:left">FHIR ConceptMap Resource, $translate operation</td>
    </tr>
  </tbody>
</table>

## \*\*\*\*

