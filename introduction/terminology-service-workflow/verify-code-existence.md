# Verify Code Existence

This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service to verify that a code exists. A typical example would be to validate that the codes contained in an incoming patient data message are, in fact, from a required code system, e.g. ICD-10 or LOINC.

Both external systems and systems inside the HIE may perform this transaction directly with the TS. The sequence diagram below shows the steps that occur for a system using this transaction.

1. Existence: Is a Concept Code present in a specified Code System. E,g., is '123XYZ' a valid Code in the ICD-10 Code System?

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
        <p>The FHIR CodeSystem validate-code operation: <a href="http://build.fhir.org/codesystem-operation-validate-code.html">http://build.fhir.org/codesystem-operation-validate-code.html</a>.
          HL7 FHIR Specifications v3.0 or higher support validate-code. The response
          is a Boolean (true or false) based on whether the code exists in the specified
          CodeSystem.</p>
        <p>This workflow implements the IHE IT Infrastructure Technical Framework
          Supplement - Sharing Valuesets, Codes, and Maps (SVCM) Transaction: Validate
          Code ITI-Y5 for Code Systems.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The required CodeSystems have been preloaded into the Terminology Service.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system or other HIE component that is requesting
            to verify a code.</li>
          <li>TS - Stores the curated official version of the terminology and codes
            for the health system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description 

The following is a description of the interaction steps. 

![](https://lh5.googleusercontent.com/tVcE12rhH8Qu9ouNomMiBBhudn6nPwbbxMhMMD4Xd3cLTErV3U-mF0d63-2tX9CDXJX3NMn9R7z1nzIOYg3rhtg0_yFgAv0bwI5YrO-YYqnbv5JmIVN7fcls68f5ULMQNw)

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
      <td style="text-align:left">Code verification request</td>
      <td style="text-align:left">
        <p>The validate-code request is triggered by a PoS or other HIE component.</p>
        <p>Input: A Concept Code and target Code System.</p>
      </td>
      <td style="text-align:left">FHIR CodeSystem Resource, $validate-code operation</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Code verification response</td>
      <td style="text-align:left">The response is sent back to the requesting system. Output: a True or
        False response.</td>
      <td style="text-align:left">FHIR CodeSystem Resource, $validate-code operation</td>
    </tr>
  </tbody>
</table>

## 

