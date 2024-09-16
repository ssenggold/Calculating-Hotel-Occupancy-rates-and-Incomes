#include <iostream>
#include <iomanip>
using namespace std;

int main() {
 
const double SINGLE_ROOM_RATE = 60.0;
 
const double DOUBLE_ROOM_RATE = 75.0;
 
const double KING_ROOM_RATE = 100.0;
 
const double SUITE_ROOM_RATE = 150.0;
 
const int MAX_FLOORS = 5;
 
const int MAX_ROOMS_PER_FLOOR = 30;
 
string location;
 
int numFloors, totalRooms = 0, totalOccupiedRooms = 0, minRooms = MAX_ROOMS_PER_FLOOR, minFloor;
 
double totalIncome = 0.0, occupancyRate;
 
cout << "Enter the location of the hotel chain: ";
 
getline(cin, location);
 
cout << "Enter the number of floors in the hotel (max 5): ";
 
cin >> numFloors;
 
while (numFloors < 1 || numFloors > MAX_FLOORS) {
 
cout << "Invalid number of floors. Please enter a number between 1 and 5: ";
 
cin >> numFloors;
 
}
 
for (int i = 1; i <= numFloors; ++i) {
 
int numRooms, occupiedRooms;
 
cout << "Enter the total number of rooms on floor " << i << " (max 30): ";
 
cin >> numRooms;
 
while (numRooms < 1 || numRooms > MAX_ROOMS_PER_FLOOR) {
 
cout << "Invalid number of rooms. Please enter a number between 1 and 30: ";
 
cin >> numRooms;
 
}
 
cout << "Enter the number of occupied rooms on floor " << i << ": ";
 
cin >> occupiedRooms;
 
while (occupiedRooms < 0 || occupiedRooms > numRooms) {
 
cout << "Invalid number of occupied rooms. Please enter a number between 0 and " << numRooms << ": ";
 
cin >> occupiedRooms;
 
}
 
totalRooms += numRooms;
 
totalOccupiedRooms += occupiedRooms;
 
totalIncome += (SINGLE_ROOM_RATE * (numRooms - occupiedRooms)
 
+ DOUBLE_ROOM_RATE * (numRooms - occupiedRooms)
 
+ KING_ROOM_RATE * (numRooms - occupiedRooms)
 
+ SUITE_ROOM_RATE * (numRooms - occupiedRooms));
 
if (numRooms < minRooms) {
 
minRooms = numRooms;
 
minFloor = i;
 
}
 
}
 
occupancyRate = (static_cast<double>(totalOccupiedRooms) / totalRooms) * 100;
 
cout << fixed << setprecision(2);
 
cout << "\nLocation: " << location << endl;
 
cout << "Total hotel income for one night: $" << totalIncome << endl;
 
cout << "Total number of occupied rooms: " << totalOccupiedRooms << endl;
 
cout << "Total number of unoccupied rooms: " << totalRooms - totalOccupiedRooms << endl;
 
cout << "Occupancy rate: " << occupancyRate << "%" << endl;
 
cout << "Floor number with the minimum number of rooms: " << minFloor << endl;
 
if (occupancyRate < 60.0) {
 
cout << "Please improve the occupancy rate." << endl;
 
}
 
return 0;
