# Expand Value Set

 This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service and retrieve the set of all Concepts in the Value Set. Rather than testing each code contained in an incoming patient data message for Value Set membership, this operation enables a component to "cache" the Value Set members and test individual membership locally, avoiding extensive network overhead. Due to the likely updating of Value Set definitions, on the other hand, components should periodically refresh their local copy of the expansion.

Both external systems and systems inside the HIE may perform this transaction directly with the TS.  The sequence diagram below shows the steps that occur for a system using this transaction.   

1. Expansion: Retrieve the set of Concept Codes that are members of the HIV Value Set.

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
        <p>The FHIR ValueSet expand operation: <a href="http://build.fhir.org/valueset-operation-expand.html">http://build.fhir.org/valueset-operation-expand.html</a>.
          HL7 FHIR Specifications v3.0 or higher support expand. The response is
          Value Set Resource that contains a collection of all the Concepts in the
          Value Set. If Concept attributes are to be returned with the collection,
          the attributes can be specified in the expand request.</p>
        <p>This workflow implements the IHE IT Infrastructure Technical Framework
          Supplement - Sharing Valuesets, Codes, and Maps (SVCM) Transaction: Expand
          Value Set ITI-Y3.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The required ValueSets and associated CodeSystems have been preloaded
        into the Terminology Service.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system or any other HIE component that is requesting
            the expansion.</li>
          <li>TS - Stores the curated, official version of the Value Set for the health
            system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description 

The following is a description of the interaction steps. 

![](https://lh6.googleusercontent.com/tzzPlEZXJf_0yFSnLH8UKDEBsMSHT7ga4d4dBhMz5D01i1SVUHyjiwmsBkDabqtJG5C1tj7A4AUH1F3oQEYWRIAi1KKNtptfpkTGZJbY7f4wUBOY4T8Ik897x--PciLPEw)

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
      <td style="text-align:left">ValueSet expansion request</td>
      <td style="text-align:left">
        <p>The expand request is triggered by a PoS or other HIE component.</p>
        <p>Input: The target ValueSet.</p>
      </td>
      <td style="text-align:left">FHIR ValueSet Resource, $expand operation</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">ValueSet expansion response</td>
      <td style="text-align:left">
        <p>The response is sent back to the requesting system.</p>
        <p>Output: a ValueSet Resource containing the list of Concept members.</p>
      </td>
      <td style="text-align:left">FHIR ValueSet Resource, $expand operation</td>
    </tr>
  </tbody>
</table>

## \*\*\*\*

