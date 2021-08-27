# Query Patient Demographic Records by Demographics Workflow \(something missing\)

## Overview

This transaction allows Point-of-Service \(PoS\) systems to query for patients that match supplied demographics. The following sequence diagram shows the steps involved.

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
        <p><b>     Mature</b>
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
        <p>Option 1</p>
        <ul>
          <li>QBP^Q22 - <a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">IHE ITI-21</a>
          </li>
          <li>RSP^K22 - <a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">IHE ITI-21</a>
          </li>
        </ul>
        <p>Option 2</p>
        <ul>
          <li>FHIR - <a href="http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm_Rev1.0_PC_2014-06-06.pdf">Patient Demographics Query IHE ITI PDQm Transaction</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The PoS system is a trusted application known by the HIE and it is registered
        with the interoperability layer to be able to send and receive data securely
        (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point of care system that captures patient identifiers, is responsible
            for sending the identifiers to the HIE.</li>
          <li>IL - Mediates the transactions between the PoS system and the client registry.</li>
          <li>CR - Manages patient demographics and identifier details</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

