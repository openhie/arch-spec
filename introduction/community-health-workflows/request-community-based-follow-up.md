# Request Community Based Follow-Up

## Overview

This workflow allows a point-of-care system to make requests to a Community Health Information System \(CHIS\) for patient follow-up.  A common implementation is for Lost to Follow-Up whereby a clinic generates a list of patients who have missed appointments for follow-up through CHIS. During the follow-up, Community Health Workers \(CHW\) encourage the identified patients to attend their appointments and seek to understand the reason for non-attendance. The follow-up process may involve a CHW physically going to find the patient or reaching out through other communication protocols such as phone call or SMS. 

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
        <p>&lt;del&gt;&lt;/del&gt;</p>
        <ul>
          <li>Workflow is defined and ARB approved</li>
          <li>Initial implementations are being discussed</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standard(s) *</td>
      <td style="text-align:left">&lt;del&gt;&lt;/del&gt;</td>
      <td style="text-align:left">FHIR</td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left">&lt;del&gt;&lt;/del&gt;</td>
      <td style="text-align:left">
        <p>&lt;del&gt;&lt;/del&gt;</p>
        <ol>
          <li>The Point-of-Service (PoS) system is a trusted application known by the
            HIE and it is registered with the interoperability layer to be able to
            send and receive data securely</li>
          <li>The Community Health Information System (CHIS) is a trusted application
            known by the HIE and it is registered with the interoperability layer to
            be able to send and receive data securely</li>
        </ol>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left">&lt;del&gt;&lt;/del&gt;</td>
      <td style="text-align:left">
        <p>&lt;del&gt;&lt;/del&gt;</p>
        <ul>
          <li><b>Point-of-Care System</b>: System that makes the request for a community
            health worker (CHW) to find and follow-up on a patient. The requesting
            system will often be an EMR like <a href="https://openmrs.org/">OpenMRS</a>.</li>
          <li><b>CHIS: </b>A Community Health Information System is an information system
            that supports the routine and emergency health care of a patient population
            within community contexts in defined geographic areas. This is often a
            mobile application.</li>
          <li><b>IOL:</b> Interoperability Layer to handle data governance and security
            issues, CSD Services Finder</li>
          <li><b>SHR: </b><a href="https://wiki.ohie.org/display/SUB/Shared+Health+Record+Community">Shared Health Record</a> is
            a centralized data repository for storing patient&#x2019;s shared health
            record.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## **Interaction Description** 

 ****

![](../../.gitbook/assets/community-based-follow-up-data-flow-4-%20%281%29.png)

| **\#** | Interaction | Data  | Transaction Options |
| :--- | :--- | :--- | :--- |
| 1 | Determine Patients Requiring Follow-up | Using an EMR or other Point-of-care system, the users will designate patients that require community-based follow-up.  This may be due to a missed appointment or other action triggering a follow-up.   |   ~~~~ |
| 2, 3 | ServiceRequest | A service request is created with "Active" status and sent through the IOL to the SHR.  The IOL may need to orchestrate use of the patient identity used in the HIE.  These steps are not shown.   | FHIR ServiceRequest |
| 4,5 | Query ServiceRequest | Query for "Active" ServiceRequest.  If necessary, the IOL can translate the patient ID.   | FHIR ServiceRequest query |
| 6,7 | Return results | The results of the query are returned.  If necessary, the IOL can translate the patient ID.   | Query response  |
| 8 | Claim Service Requests | Through use of the CHIS, the end users may determine which ServiceRequests for follow-up or other community services that they are going to address,   |  |
| 9, 10 | Update Service Request | Claimed service requests will be set to "On Hold" status.   | FHIR ServiceRequest |
| 11 | Alert CHW \(optional\) | See [Alerting / Sending Reminders or Information](../alerting-sending-reminders-or-information/) for a description of this workflow |  |
| 12 | Follow up in CHIS |  |  |
| 13 | Save patient data | See [Save Patient-level Clinical Data Workflow](../shared-health-record/save-patient-level-clinical-data-workflow.md) |  |
| 14 | Update Service Request | Claimed ServiceRequest will be set to "Complete" status.   | FHIR ServiceRequest |
| 15, 16 | Query ServiceRequest | Status "completed"  | FHIR ServiceRequest query |
| 17, 18 | Return results |  |  |
| 19 | Update CHIS |  |  |



