# Update Patient Demographic Record Workflow

## Overview

This transaction allows the Point-of-Service \(PoS\) systems to update a patient record in the client registry. The following sequence diagram shows the steps involved.

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
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">ADT^A08 - <a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">IHE ITI-8</a> Transactions</td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>The Point-of-Service system is a trusted application known by the HIE
            and it is registered with the interoperability layer to be able to send
            and receive data securely (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</li>
          <li>The Patient to be updated is assumed to already exist in the Client Registry.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>PoS - The point of care system that captures patient identifiers, is responsible
            for sending the identifiers to the HIE.</li>
          <li>IL - Mediates the transactions between the PoS system and the Client Registry.</li>
          <li>CR - Manages patient demographics and identifier details.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

The following is a description of the interaction steps. 

![](https://lh3.googleusercontent.com/LPkYsrvX4ygNHxQwkssyYliNGHGUBuyDo9h4TXrP4cHC6881jdodNXLynSaNWCqZz4Khhosk7o4H2NKpjTDcV83DW_2xoIhWCOiteO5mbb_Ch-V7mmlEbTBcwfAHXJhz4A)

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
      <td style="text-align:left">Update patient</td>
      <td style="text-align:left">The format of the message is specified by the ITI-8 IHE PIX v2 transaction
        and takes the form of an HL7v2.3.1 A08 message. The message may include
        both identifiers and demographic attributes for the patient to be updated.</td>
      <td
      style="text-align:left">
        <p>PIF ITI-8 transaction ADT^A08</p>
        <p><a href="https://wiki.ohie.org/display/documents/Patient+Identity+Feed+IHE+ITI-8+Transactions">Patient Identity Feed IHE ITI-8 Transactions</a>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Update patient</td>
      <td style="text-align:left">The message from the Point-of-Service system is passed directly through
        to the CR by the IL.</td>
      <td style="text-align:left">PIF ITI-8 transaction ADT^A08 <a href="https://wiki.ohie.org/display/documents/Patient+Identity+Feed+IHE+ITI-8+Transactions">Patient Identity Feed IHE ITI-8 Transactions</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Acknowledge patient updated</td>
      <td style="text-align:left">The response message is an HL7 ACK. See ITI TF-2x: C.2.3, &quot;Acknowledgment
        Modes&quot; for definition and discussion of the ACK message.</td>
      <td style="text-align:left">PIF ITI-8 transactions HL7 ACK <a href="https://wiki.ohie.org/display/documents/Patient+Identity+Feed+IHE+ITI-8+Transactions">Patient Identity Feed IHE ITI-8 Transactions</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Acknowledge patient updated</td>
      <td style="text-align:left">The message from the CR is passed directly through to the PoS by the IL.</td>
      <td
      style="text-align:left">PIF ITI-8 transactions HL7 ACK <a href="https://wiki.ohie.org/display/documents/Patient+Identity+Feed+IHE+ITI-8+Transactions">Patient Identity Feed IHE ITI-8 Transactions</a>
        </td>
    </tr>
  </tbody>
</table>

## \*\*\*\*

