# Query Concept Maps

 This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service to query for Concept Maps.  A typical example would be to request the set of Concept Maps whose target Code System is SNOMED CT. Mapping is frequently required when patient data is collected using Concepts/Codes from one Code System but the data must be reported or aggregated, say for decision support, in a different Code System. The set of such associated Concepts, usually for a specific use-case, are stored in the Terminology Service in a FHIR Resource called a ConceptMap.

Both external systems and systems inside the HIE may perform this transaction directly with the TS. The sequence diagram below shows the steps that occur for a system using this transaction.   

1. Query Concept Maps: What Concept Maps have a map target of 'SNOMED CT''?

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
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
        <p></p>
        <ul>
          <li>One or more OpenHIE implementations of this workflow exist in one or more
            countries</li>
          <li>Workflow is defined and ARB approved</li>
          <li>Workflow is supported by mature standards</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The required Concept Maps have been preloaded into the Terminology Service.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system or other HIE component that is that
            is querying for Concept Maps.</li>
          <li>TS - Stores the curated, official version of the Concept Maps for the
            health system.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description 

The following is a description of the interaction steps.

![](https://lh4.googleusercontent.com/lMBBRqFL2VgXeCrFBOPH-K-sDVo4hHqwW7gP7wxjyYAwbDHAITnWIGb3eddt6CQDVPCGPq3V56kCGENMV17f0WjgWxJ7R-XWpAX_l2nKoEGMr-_GDoPEd927PHERFR27QQ)

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
      <td style="text-align:left">Query Concept Map request</td>
      <td style="text-align:left">
        <p>The Concept Map search request is triggered by a PoS or other HIE component.</p>
        <p>Input: A set of FHIR search parameters.</p>
      </td>
      <td style="text-align:left">FHIR ConceptMap Resource</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Query Concept Map response</td>
      <td style="text-align:left">
        <p>The response is sent back to the requesting system.</p>
        <p>Output: a Bundle of ConceptMap Resources that satisfy the search parameters.</p>
      </td>
      <td style="text-align:left">FHIR ConceptMap Resource</td>
    </tr>
  </tbody>
</table>

## 

