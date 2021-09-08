# Query Patient Demographic Records by Identifier Workflow

## Overview

This transaction allows patient demographics to be fetched from the Client Registry using an identifier. The following sequence diagram shows the steps involved.

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
        <p> <b>Mature</b>
        </p>
      </th>
      <th style="text-align:left">
        <ul>
          <li><b>One or more OpenHIE implementations of this workflow exist in one or more countries</b>
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
        <ul>
          <li>Option 1
            <ul>
              <li><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">QBP^Q22 - IHE ITI-21</a>
              </li>
              <li><a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">RSP^K22 - IHE ITI-21</a>
              </li>
            </ul>
          </li>
          <li>Option 2
            <ul>
              <li>FHIR - <a href="http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm_Rev1.0_PC_2014-06-06.pdf">Patient Demographics Query IHE ITI PDQm Transaction</a>
              </li>
            </ul>
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
        <ul>
          <li>PoS - The point of service system that captures patient identifiers, is
            responsible for sending the identifiers to the HIE.</li>
          <li>IL - Mediates the transactions between the PoS system and the client registry.</li>
          <li>CR - Manages patient demographics and identifier details.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description**

The following is a description of the interaction steps.

![](https://lh4.googleusercontent.com/E7KhcHt2R43LmqTGoZdoOa9aL-Oek0lKdOOZrsF8LUc8kM1Edo7FzujmTK9wNstLUpXKLcG7QfQ8IWP8gMQK45nbXYxvSetQ49irKJ_sk7aJxF_r8nlkYAKYB-dkot0B2Q)

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
      <td style="text-align:left">Get patient by identifier</td>
      <td style="text-align:left">The message includes the query criteria, which may include one or more
        patient identifiers.</td>
      <td style="text-align:left">
        <ul>
          <li><a href="https://wiki.ohie.org/display/documents/Patient+Demographics+Query+IHE+ITI-21+Transaction">PDQ ITI-21 transaction QBP-Q22</a>
          </li>
        </ul>
        <p>OR</p>
        <ul>
          <li><a href="http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm_Rev1.0_PC_2014-06-06.pdf">Patient Demographics Query IHE ITI PDQm Transaction</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Get patient from CR by identifier</td>
      <td style="text-align:left">The message from the PoS is passed directly through to the CR by the IL</td>
      <td
      style="text-align:left">
        <ul>
          <li><a href="https://wiki.ohie.org/display/documents/Patient+Demographics+Query+IHE+ITI-21+Transaction">PDQ ITI-21 transaction QBP-Q22</a>
          </li>
        </ul>
        <p>OR</p>
        <ul>
          <li><a href="http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_PDQm_Rev1.0_PC_2014-06-06.pdf">Patient Demographics Query IHE ITI PDQm Transaction</a>
          </li>
        </ul>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Return patient record</td>
      <td style="text-align:left">The response returns the patient(s) that matched the query criteria. It
        may consist of zero or more patient demographic records.</td>
      <td style="text-align:left">
        <ul>
          <li><a href="https://wiki.ohie.org/display/documents/Patient+Demographics+Query+IHE+ITI-21+Transaction">PDQ ITI-21 transaction RSP-K22</a>
          </li>
        </ul>
        <p>OR</p>
        <ul>
          <li>Query Patient Resource Response (<a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">ITI TF-2</a>c:3.Y1.4.2):
            Bundle (Patient)</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Return patient record</td>
      <td style="text-align:left">The message from the CR is passed directly through to the PoS by the IL</td>
      <td
      style="text-align:left">
        <ul>
          <li><a href="https://wiki.ohie.org/display/documents/Patient+Demographics+Query+IHE+ITI-21+Transaction">PDQ ITI-21 transaction RSP-K22</a>
          </li>
        </ul>
        <p>OR</p>
        <ul>
          <li>Query Patient Resource Response (<a href="https://www.ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_TF_Vol2a.pdf">ITI TF</a>-2c:3.Y1.4.2):
            Bundle (Patient)</li>
        </ul>
        </td>
    </tr>
  </tbody>
</table>

## \*\*\*\*

