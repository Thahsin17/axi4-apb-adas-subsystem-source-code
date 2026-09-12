# axi4-apb-adas-subsystem-source-code
AXI4-to-APB Communication Subsystem IP for ADAS.
# axi4-apb-adas-subsystem-source-code

AXI4-to-APB Communication Subsystem IP for ADAS.

## 1. Software Required

- Python 3.x
- Cocotb
- HDL simulator compatible with Cocotb
- Git

## 2. Program Execution

This project uses a Python-based Cocotb testbench to verify the
AXI4-to-APB Communication Subsystem IP.

### Step 1: Clone the Repository

git clone https://github.com/Thahsin17/axi4-apb-adas-subsystem-source-code.git

cd axi4-apb-adas-subsystem-source-code

### Step 2: Install Cocotb

pip install cocotb

### Step 3: Run the Cocotb Testbench

The Python testbench is executed together with the RTL design
using the HDL simulator configured for the project.

The testbench performs:

1. AXI4 write transaction
2. AXI4-to-APB communication
3. AXI4 read transaction
4. Read data verification
5. Comparison of expected and actual data
6. PASS/FAIL reporting

### Step 4: Check the Simulation Output

A successful test produces:

RESULT : PASS

The testbench is considered successful when the expected data
matches the received read data.

## 3. Input Format

The testbench applies AXI4 write transactions using a 32-bit
address and 32-bit hexadecimal data values.

Main test address:

0x40000000

Example input data:

0x00000055
0x000000AA
0x00000012
0x0000000F
0x0000007F
0x00000080
0x12345678
0x55555555
0xAAAAAAAA
0xDEADBEEF

After each write transaction, an AXI4 read transaction is issued
using the same address. The returned data is compared with the
expected data.

## 4. Expected Output

For each test case, the simulation displays:

- AXI4 read request address
- AXI4 address handshake
- AXI4 read response data
- AXI4 read response status
- Expected data
- Actual read data
- Test result

Example:

AXI READ REQUEST  addr = 0x40000000
AR HANDSHAKE      addr = 0x40000000
AXI READ RESPONSE RDATA = 0x00000055
AXI READ RESPONSE RRESP = 00
EXPECTED DATA     : 0x00000055
READ DATA         : 0x00000055
RESULT            : PASS

The expected output is obtained when the expected data and read
data are identical.

## 5. Important Parameters

- Programming language: Python
- Verification framework: Cocotb
- Interface: AXI4-to-APB
- AXI4 data width: 32 bits
- Test address: 0x40000000
- Input data format: 32-bit hexadecimal values
- Verification type: AXI4 read/write transaction testing
- Expected result: PASS when read data matches expected data

## 6. Test Results

The Cocotb verification successfully tests multiple AXI4
write/read transactions.

Example test results:

Write Data        Expected Data       Read Data       Result

0x00000055        0x00000055          0x00000055      PASS
0x000000AA        0x000000AA          0x000000AA      PASS
0x00000012        0x00000012          0x00000012      PASS
0x0000000F        0x0000000F          0x0000000F      PASS
0x00000000        0x00000000          0x00000000      PASS
0x0000007F        0x0000007F          0x0000007F      PASS
0x00000080        0x00000080          0x00000080      PASS
0x12345678        0x00000078          0x00000078      PASS
0xAAAAAAAA        0x000000AA          0x000000AA      PASS
0x55555555        0x00000055          0x00000055      PASS
0xDEADBEEF        0x000000EF          0x000000EF      PASS

Overall Result: PASS
