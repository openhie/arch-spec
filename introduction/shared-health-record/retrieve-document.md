# Retrieve Document



This transaction can be used to retrieve documents from a SHR or document repository that stores health records.  In addition, a vaccine verifier \(point-of-care application or any authorized application outside of the HIE\) can use this transaction to  verify a Digital Documentation COVID Certificate \(DDCC\) Immunization event.  This may include COVID immunizations and negative tests.  

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg"
          alt/>
        </p>
        <p><b>Newly Defined</b>
        </p>
      </th>
      <th style="text-align:left">
        <p></p>
        <ul>
          <li><b>Workflow is defined by WHO and has OpenHIE ARB approval</b>
          </li>
          <li><b>Initial implementations are being considered.  </b>
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
        <p></p>
        <ul>
          <li>The Retrieve Health Certificate transaction is based on <a href="https://profiles.ihe.net/ITI/MHD/ITI-68.html">MHD&apos;s Retrieve Document transaction [ITI-68]</a>.
            It can be used to verify the contents of a DDCC Immunization event.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>The appropriate trust agreements and processes have been put in place
            for the document requester or Verifier to receive the certificate.</li>
          <li>The appropriate documents or meta data about the document have been stored.
            This may include saving a vaccine or a lab test event to a shared health
            record via <a href>Register / Store Document</a> or <a href="save-patient-level-clinical-data-workflow.md">Save Patient-level Clinical Data Workflow</a>.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>Document Requester or Verifier (External System) - External system or
            Point-of-care system requesting the document or vaccine status.</li>
          <li><a href="../../openhie-component-specifications-1/openhie-interoperability-layer-iol.md">IOL</a> -
            The interoperability layer that secures and orchestrates the exchange of
            information</li>
          <li><a href="../../openhie-component-specifications-1/openhie-shared-health-record-shr.md">SHR </a>/
            Document Repository (or Electronic Vaccination Registry) - The shared health
            record that serves as a centralized data store for patients&#x2019; longitudinal
            health record and or health documents</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

### Interaction Description

The Interaction Description is stored in the ["Retrieve Health Certificate Reference" in the WHO FHIR IG](https://worldhealthorganization.github.io/ddcc/transactions.html).  

{% hint style="success" %}
References:  [WHO DDCC Workflo](https://worldhealthorganization.github.io/ddcc/workflows.html)
{% endhint %}

