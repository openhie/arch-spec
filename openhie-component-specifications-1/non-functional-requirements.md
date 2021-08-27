# Non-Functional Requirements

The following are recommended non-functional requirements for the OpenHIE component software depicted in the gray box of figure 2.1 and further defined in this document. OpenHIE supports the use of technology that is appropriate for the use case and does not preclude the use of proprietary tools but rather supports the use of tools that are built to meet the needs and support the implementation. OpenHIE does require that technologies do not create a “lock-in” scenario whereby the implementer has no access to their data and as such supports an approach to an open architecture.

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>#</b>
      </th>
      <th style="text-align:left">OpenHIE Non-Functional Requirements</th>
      <th style="text-align:left"><b>Recommendation/ Requirement</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>NRF-1</b>
      </td>
      <td style="text-align:left">Technologies should provide standard means of accessing data within the
        system that does not lock the client into proprietary data formats or storage
        mechanisms.</td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>NFR-2</b>
      </td>
      <td style="text-align:left">
        <p>The system should be well Documented: An OpenHIE reference system should
          include appropriate background, design, installation, configuration, and
          operational documentation to ensure it is easy to understand, maintain,
          and debug.</p>
        <ol>
          <li>Source code should have comments so that developers do not need to look
            anywhere else to understand the code.</li>
          <li>Configuration files should have embedded comments explaining the different
            options.</li>
          <li>Installation, configuration, and operational activities should be described.</li>
        </ol>
      </td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>NFR-3</b>
      </td>
      <td style="text-align:left">If the system is an open source tool the system should have open, easy
        access to source code: A standard version control system (e.g., GitHub)
        should be used to ensure that source code access is fast, easy to download,
        compile, and execute code.</td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>NFR-4</b>
      </td>
      <td style="text-align:left">
        <p>The system should be built using common technology:</p>
        <ol>
          <li>In order to make it easy to run/configure/debug, the software should be
            built on popular technologies that are widely accepted.</li>
          <li>Any 3rd party libraries used by the software should be easy for a typical
            developer to use.</li>
          <li>Any external software/systems (like the database) should also be easy
            to use.</li>
          <li>It should be easy to view the contents of the database.</li>
        </ol>
      </td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>NFR-5</b>
      </td>
      <td style="text-align:left">The source code should include unit tests that are based on the specific
        requirements of OpenHIE and that create a framework to validate functionality
        and that the system operates as designed.</td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>NFR-6</b>
      </td>
      <td style="text-align:left">OpenHIE does not preclude the use of proprietary solutions. If an open
        source solution is selected it is recommended that the component would,
        ideally, be distributed under an OSI approved open-source license that
        minimizes complexity and enables an implementer community to leverage the
        software in a broad variety of sustainability contexts.</td>
      <td style="text-align:left">Recommendation</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>NFR-7</b>
      </td>
      <td style="text-align:left">The system should take into account the IT infrastructure of low resource
        settings where electricity, internet and/or technical literacy may be limited.</td>
      <td
      style="text-align:left">Recommendation</td>
    </tr>
  </tbody>
</table>

