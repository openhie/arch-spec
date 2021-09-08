# Validate and Save Aggregate Data

This workflow specifies the interactions for validating and saving an aggregate data message that has been transmitted from an external system to the HIE.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>Workflow Maturity</b>
      </th>
      <th style="text-align:left">
        <p>
          <img src="https://lh5.googleusercontent.com/Jhlle6_MgJyrv7qJwksD4lSccNcIeIAmz3vJprq5F7s45EYyqm-y1OXrxhVZ3ZTF9yXt7521LYuCIaWOKm6QlUd9VswR0K3j6VhdwbKbSFOOJ6e35FxAWoAr1DedC80Okg"
          alt/>
        </p>
        <p> <b>Maturing</b>
        </p>
      </th>
      <th style="text-align:left">
        <ul>
          <li>Workflow is defined and ARB approved</li>
          <li>Workflow is supported by emerging IHE ADX standard</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Standards*</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">ADX for structuring aggregate data - <a href="http://www.ihe.net/uploadedFiles/Documents/QRPH/IHE_QRPH_Suppl_ADX.pdf">http://www.ihe.net/uploadedFiles/Documents/QRPH/IHE_QRPH_Suppl_ADX.pdf</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Assumptions and Prerequisites</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">The sender and receiver have the same metadata (indicator, disaggregators
        and facilities). If not, the metadata will need to be translated.</td>
    </tr>
    <tr>
      <td style="text-align:left">Actors</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">
        <p><b>Sender - External System Actor</b>
        </p>
        <ul>
          <li>The system <b>sending</b> the ADX message. The system may be a Health Information
            Exchange with patient-level abilities to aggregate data and/or a system
            that contains aggregate level data. The system may also be a point-of-service
            system that contains or produces aggregate data.</li>
        </ul>
        <p><b>Receiving HIE</b>
        </p>
        <ul>
          <li>IL -The Interoperability Layer (IL) is the component that enables easier
            interoperability between disparate information systems by connecting the
            infrastructure services and client applications together. An interoperability
            layer receives transactions from the external system and coordinates interaction
            between components of the HIE and provides common core functions to simplify
            the interoperability between systems.</li>
          <li>HMIS - Health Management Information System that is processing and storing
            the aggregate data (ADX message) <b>received.</b>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Interaction Description

![](https://lh6.googleusercontent.com/BlXalgCia-nuCuMsYCeMy7QqMzEvmAE4V7JQ7mVTgpGgyYetQxjVIp1fVg1ms9rHvtuXNc-JBJEGk1DJixqOKX5XYcWwHx6FY3uTl58pPJ3g35qTQwnbwMl4GsP7aoDUlg)

<table>
  <thead>
    <tr>
      <th style="text-align:left">#</th>
      <th style="text-align:left"><b>Interaction</b>
      </th>
      <th style="text-align:left"><b>Data / Notes</b>
      </th>
      <th style="text-align:left"><b>Transaction Options</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">1</td>
      <td style="text-align:left">
        <p>Receive Aggregate Data Message</p>
        <p>(The process is initiated by the receipt of an Aggregate Data Message.)</p>
      </td>
      <td style="text-align:left">ADX data</td>
      <td style="text-align:left">ADX - <a href="http://www.ihe.net/uploadedFiles/Documents/QRPH/IHE_QRPH_Suppl_ADX.pdf">http://www.ihe.net/uploadedFiles/Documents/QRPH/IHE_QRPH_Suppl_ADX.pdf</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">2</td>
      <td style="text-align:left">Ensure sender is authenticated and log a copy of the message</td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">3</td>
      <td style="text-align:left">Route message to the HMIS</td>
      <td style="text-align:left">Implementation choice: Implementers may select to validate the aggregate
        data message with a DSD before routing it to the HMIS.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">4</td>
      <td style="text-align:left">Process the ADX Message</td>
      <td style="text-align:left">Implementation requirements: Each implementation may have specified rules
        or data checks that are performed on the message as it is imported into
        the system. These checks may include data/metadata checks, numerator and
        denominator checks and checks to be sure that reporting entities reported
        on the desired indicators.</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">5</td>
      <td style="text-align:left">(Optional) Generate processing response</td>
      <td style="text-align:left">The current ADX standard does not specify a processing response.</td>
      <td
      style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">6</td>
      <td style="text-align:left">
        <p>(Optional)</p>
        <p>Log the processing response and return it to the ADX</p>
      </td>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>

