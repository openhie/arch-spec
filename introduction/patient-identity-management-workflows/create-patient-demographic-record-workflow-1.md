# Create Patient Demographic Record Workflow

## Overview

This transaction allows a Point-of-Service \(PoS\) system to store a patient's demographics in the Client Registry. The following sequence diagram below shows the steps that occur during this transaction.

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
        <p><b>    Mature</b>
        </p>
      </th>
      <th style="text-align:left">
        <p></p>
        <ul>
          <li>Workflow is defined and ARB approved</li>
          <li>Workflow is supported by mature standards</li>
          <li>One or more OpenHIE implementations of this workflow exist in one or more
            countries</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standard(s) *</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">ADT^A01, ADT^A04, ADT^A05 - PIF IHE ITI-8 Transactions</td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ol>
          <li>The Point-of-Service (PoS) system is a trusted application known by the
            HIE and it is registered with the interoperability layer to be able to
            send and receive data securely (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</li>
          <li>The workflow will result in a positive acknowledgement message when the
            patient is successfully created in the Client Registry or if the patient
            already exists in the Client Registry.</li>
          <li>The workflow will not register a duplicate patent if the patient already
            exists in the Client Registry.</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point-of-service system that captures patient identifiers, is
            responsible for sending the identifiers to the HIE.</li>
          <li>IL - Mediates the transactions between the PoS system and the Client Registry.</li>
          <li>CR - Manages patient demographics and identifier details.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

![](https://lh6.googleusercontent.com/ZCc85rW_nQsY-AJmFI-8dWI5BigoEFSmBGUbx0-raNxdsgKVABuEcgJUF8dOK1HUA2sBFojGQ5iWgVRGfxlwzQwJBZZhGIu5u7sV2dAdmQ0SSAHq8LOlBTjhyjPn_Goijw)

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>#</b>
      </th>
      <th style="text-align:left">Interaction</th>
      <th style="text-align:left">Data</th>
      <th style="text-align:left">Transaction Options</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">Register Patient (Demographics)</td>
      <td style="text-align:left">The message may include both identifiers and demographic attributes for
        the patient to be registered. The format of the message is specified by
        the ITI-8 IHE PIX v2 transaction and takes the form of an HL7v2.3.1 A01
        (Admission of an in-patient into a facility), A04 (Registration of an outpatient
        for a visit of the facility), or A05 (registration of patient information
        ahead of actual admission) message depending on whether the message is
        the result of admitting and in-patient into a facility, registering an
        outpatient, or pre-admission of an in-patient.</td>
      <td style="text-align:left">
        <p>PIF ITI-8 transactions ADT^A01, ADT^A04, ADT^A05</p>
        <p><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">Patient Identity Feed IHE ITI-8 Transactions</a>
          <br
          />
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Register Patient (Demographics)</td>
      <td style="text-align:left">The message from the PoS is passed directly through to the CR by the IL.</td>
      <td
      style="text-align:left">
        <p>PIF ITI-8 transactions ADT^A01, ADT^A04, ADT^A05</p>
        <p><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">Patient Identity Feed IHE ITI-8 Transactions</a>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Acknowledge patient is in the CR</td>
      <td style="text-align:left">The response message is an HL7 ACK. See ITI TF-2x: C.2.3, &quot;Acknowledgment
        Modes&quot; for definition and discussion of the ACK message.</td>
      <td style="text-align:left">
        <p>PIF ITI-8 transactions HL7 ACK</p>
        <p><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">Patient Identity Feed IHE ITI-8 Transactions</a>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Acknowledge patient is in the CR</td>
      <td style="text-align:left">The message from the CR is passed directly through to the Point-of-Service
        by the IL.</td>
      <td style="text-align:left">
        <p>PIF ITI-8 transactions HL7 ACK</p>
        <p><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">Patient Identity Feed IHE ITI-8 Transactions</a>
        </p>
      </td>
    </tr>
  </tbody>
</table>

