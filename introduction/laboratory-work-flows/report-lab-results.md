# Report Lab Results

A laboratory information system \(LIS\) can send lab test results to an Electronic Medical Record \(EMR\) system.

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
        <ul>
          <li>Workflow is defined and ARB approved</li>
          <li>Initial implementations are being implemented</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <ul>
          <li>FHIR R4 Workflow</li>
          <li>FHIR R4 search on Task, DiagnosticReport, ServiceRequest or Patient resources</li>
          <li>FHIR R4 bundle search response</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
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

![](https://lh3.googleusercontent.com/jaFnDthLcquyqr0od9FNVobs1RxK5xaXZQ6ixemAzUHB3Dd0PcNMqm-2tmcnMV_U_M_OHH5vZmC92cdQnJqN311AWvP_Acv9Pc-pNE2Wm1T_W4F5BNRm4XkOjpOA91TuUw)

| \# | **Interaction** | **Data** | Transaction Options |
| :--- | :--- | :--- | :--- |
| 1 | Results Saved and FHIR Task Updated | The results save generates a FHIR R4 DiagnosticReport Resource \([example](https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.rdb5qcec7z1h)\) with referenced FHIR R4 Observation resources \([example](https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.jridzznwrp75)\) to store the results,  and a reference to the associated Patient and Task Resource. |  |
| 2 | Search for Updated FHIR Tasks |  | FHIR R4 Search for Tasks based on tasks for which the owner is the EMR, and which have a status ‘completed’ |
| 3 | Return FHIR Updated Tasks | FHIR R4 Task Resource with status ‘completed’ and reference to FHIR R4 DiagnosticReport | FHIR R4 bundle search response \([example](https://docs.google.com/document/d/10cEBED1abA2s8LWFzLDWldv4j25pByQF8K2oZfhHB24/edit?ts=5f245ba3#heading=h.avnpgs9wlolc)\) |
| 4 | Search for Associated Diagnostic Reports |  | FHIR R4 Search for DiagnosticReports by UUID |
| 5 | Return Associated Diagnostic Reports | FHIR R4 DiagnosticReport Resource with |  |
| 6 | Update FHIR Task Status, Store DiagnosticReports and Save Results |  |  |

