# Order Laboratory Test

Electronic Medical Records \(EMRs\) systems can send an electronic lab order to a laboratory information system \(LIS\).

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
          <li><b>Workflow is defined and ARB approved</b>
          </li>
          <li><b>Initial implementations are being implemented</b>
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
          <li>FHIR R4 search on Task, DiagnosticReport, ServiceRequest or Patient resources</li>
          <li>FHIR R4 bundle search response</li>
          <li>FHIR R4 Workflow</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>The EMR and LIS are trusted applications known by the IOL</li>
          <li>The IOL supports node authentication, audit tracking, and rerunning of
            failed transactions</li>
          <li>The SHR adheres to OHIE specification</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li>EMR - The electronic medical record system that captures the patient and
            order information and sends the electronic order to the LIS</li>
          <li>LIS - The laboratory information system that pulls order information,
            processes orders, updating statuses and generating results sets</li>
          <li>IOL - The interoperability layer that secures and orchestrates the exchange
            of information (see OHIE Interoperability layer)</li>
          <li>SHR - The shared health record that serves as a centralized data store
            for patients&#x2019; longitudinal health record</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

![](https://lh6.googleusercontent.com/rmStLcHds3HOuCnVpcLYt6-3RIRWbR2jCa-s7jsKWQnvcdXo37rxEM23xYKsid4Qz6lVa2A2t2rZ_9742sX_mVGAQ5htfn9BYVcCRV0-06PPx--UAi6iXcx1Mr7blm6fqQ)

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
      <td style="text-align:left">Create Lab Order</td>
      <td style="text-align:left">The order save generates a FHIR R4 Task Resource (<a href="https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.xk6hg1i1g2xp">see example here</a>)</td>
      <td
      style="text-align:left">Alternatively, the order save could generate a FHIR R4 ServiceRequest
        Resource for direct transmission.</td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Send New Lab Order</td>
      <td style="text-align:left">FHIR Task bundled order is sent to the IOL and consists of a FHIR R4 Task
        Resource and a referenced FHIR R4 Patient Resource (<a href="https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.j3gsupx1n06l">example</a>).
        Task status is aligned with the FHIR workflow communication pattern found
        <a
        href="https://www.hl7.org/fhir/workflow-communications.html#12.6.2.1">here</a>
      </td>
      <td style="text-align:left">
        <p>FHIR R4 bundle (<a href="https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.jhmys02ttr9r">example</a>)</p>
        <p>Alternatively a FHIR R4 ServiceRequest and Patient Resource bundle could
          be sent
          <br />
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">3,4</td>
      <td style="text-align:left">Send New Lab Order</td>
      <td style="text-align:left">Bundled order is routed through the IOL to both the SHR and the LIS</td>
      <td
      style="text-align:left">FHIR R4 bundle (<a href="https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.jhmys02ttr9r">example</a>)</td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">Save Order and Update Order Status</td>
      <td style="text-align:left">FHIR R4 Task Resource Status is updated locally to either rejected or
        accepted. A FHIR R4 ServiceRequest Resource (<a href="https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.dq3fj8djmi9i">example</a>)
        is created for order processing with a reference to the associated task.
        EMR test requests and LIS orders are matched based on LOINC codes.</td>
      <td
      style="text-align:left">Alternatively, a ServiceRequest with a link to the referenced ServiceRequest
        could be populated.</td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">Send Order Update</td>
      <td style="text-align:left">Update Task Resource Status from [5] is sent to the IOL</td>
      <td style="text-align:left">Alternatively, this could be an update to a FHIR R4 ServiceRequest resource</td>
    </tr>
    <tr>
      <td style="text-align:left">7,8</td>
      <td style="text-align:left">Send Order Update</td>
      <td style="text-align:left">IOL routes the updated FHIR R4 Tasks to the SHR and the EMR</td>
      <td style="text-align:left">See transaction options [6]</td>
    </tr>
    <tr>
      <td style="text-align:left">9</td>
      <td style="text-align:left">Update FHIR Task Status</td>
      <td style="text-align:left">FHIR task status updated locally</td>
      <td style="text-align:left">See transaction options [6]</td>
    </tr>
  </tbody>
</table>

## \*\*\*\*

