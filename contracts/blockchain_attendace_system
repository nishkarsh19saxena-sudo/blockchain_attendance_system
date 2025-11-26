// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Project {
    address public admin;

    struct AttendanceRecord {
        uint256 timestamp;
        string subject;
        bool present;
    }

    mapping(address => bool) public isStudent;
    mapping(address => AttendanceRecord[]) public attendance;

    constructor() {
        admin = msg.sender;
    }

    // Add a student to the system
    function addStudent(address student) public {
        require(msg.sender == admin, "Only admin can add students");
        isStudent[student] = true;
    }

    // Mark attendance for a student
    function markAttendance(address student, string memory subject) public {
        require(isStudent[student], "Not a registered student");

        attendance[student].push(
            AttendanceRecord(block.timestamp, subject, true)
        );
    }

    // View attendance records of a student
    function getAttendance(address student) public view returns (AttendanceRecord[] memory) {
        return attendance[student];
    }
}
