# Verify Code Membership

This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service to verify that a code is a member of defined value set. A typical example would be to validate that the codes contained in an incoming patient data message are, in fact, from a required value set, e.g. the HIV ValueSet.

Both external systems and systems inside the HIE may perform this transaction directly with the TS. The sequence diagram below shows the steps that occur for a system using this transaction.   

1. Membership: Is a Concept Code present in a specified Value Set, e.g., is Code '123XYZ' from ICD-10 a member of the HIV ValueSet?

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
      <td style="text-align:left">Standards</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p>The FHIR ValueSet validate-code operation: <a href="http://build.fhir.org/codesystem-operation-validate-code.html">http://build.fhir.org/valueset-operation-validate-code.html</a>.
          HL7 FHIR Specifications v3.0 or higher support validate-code. The response
          is a Boolean (true or false) based on whether the code is a member of the
          specified ValueSet.</p>
        <p>This workflow implements the IHE IT Infrastructure Technical Framework
          Supplement - Sharing Valuesets, Codes, and Maps (SVCM) Transaction: Validate
          Code ITI-Y5 for Value Sets.</p>
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
          <li>PoS - The point-of-service system or other HIE component that is requesting
            to verify a code.</li>
          <li>TS - Stores the curated, official version of the Value Set for the health
            system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description 

The following is a description of the interaction steps. 

![](https://lh4.googleusercontent.com/4-iRcNlezqHnwXPGLWPfKodFiGmHUDdrk-5nUahxqNQBoKrmiw64-qTyh5sgf9XU-1LsUmSQyJxQ-LZQnxBdz3Sxre8KpN1JBnHlH8qKmjINiCVawyB9FLEU19iYdA-rEQ)

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
      <td style="text-align:left">Code verification request</td>
      <td style="text-align:left">
        <p>The validate-code request is triggered by a PoS or other HIE component.</p>
        <p>Input: A Concept Code, associated Code System and target ValueSet.</p>
      </td>
      <td style="text-align:left">FHIR ValueSet Resource, $validate-code operation</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Code verification response</td>
      <td style="text-align:left">
        <p>The response is sent back to the requesting system.</p>
        <p>Output: a True or False response.</p>
      </td>
      <td style="text-align:left">FHIR ValueSet Resource, $validate-code operation</td>
    </tr>
  </tbody>
</table>

## 

