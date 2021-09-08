# Register / Store Document

This transaction can be used to register the document metadata and optionally store documents in a SHR or document repository. This transaction can also be used to support storage of vaccine certificates.  

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
          <li>The Register / Store Document transaction is based on <a href="https://profiles.ihe.net/ITI/MHD/ITI-65.html#2365412-message-semantics">MHD&apos;s Provide Document Bundle transaction [ITI-65]</a>.
            It can be used store the metadata about a document and optionally store
            the document itself.</li>
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
            for the system sharing the document or the Document Generation Service
            to provide the documentation to the SHR or document repository.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>Point-of-Care or Document Generation Service (External System) - External
            system or Point-of-care system generating the document.</li>
          <li><a href="../../openhie-component-specifications-1/openhie-interoperability-layer-iol.md">IOL </a>-
            The interoperability layer that secures and orchestrates the exchange of
            information (see OHIE Interoperability layer)</li>
          <li><a href="../../openhie-component-specifications-1/openhie-shared-health-record-shr.md">SHR</a> /
            Document Repository (or Electronic Vaccination Registry) - The shared health
            record that serves as a centralized data store for patients&#x2019; longitudinal
            health record and or health documents</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

### Interaction Description

The Interaction Description is stored in the ["Store Health Certificate"](https://worldhealthorganization.github.io/ddcc/transactions.html#store-health-certificate) in the WHO FHIR IG.  

{% hint style="success" %}
References:  

* [WHO DDCC Workflows](https://worldhealthorganization.github.io/ddcc/workflows.html)
* [Digitize Vaccine Event](https://worldhealthorganization.github.io/ddcc/workflows.html)
{% endhint %}



