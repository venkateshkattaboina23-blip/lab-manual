import java.util.*;

class UndergroundSystem {

    private Map<Integer, Pair> checkInMap;
    
    private Map<String, double[]> travelMap;

    public UndergroundSystem() {
        checkInMap = new HashMap<>();
        travelMap = new HashMap<>();
    }

    public void checkIn(int id, String stationName, int t) {
        checkInMap.put(id, new Pair(stationName, t));
    }

    public void checkOut(int id, String stationName, int t) {
        Pair checkInData = checkInMap.get(id);
        String startStation = checkInData.station;
        int startTime = checkInData.time;

        String route = startStation + "-" + stationName;
        int travelTime = t - startTime;

        travelMap.putIfAbsent(route, new double[]{0, 0});
        travelMap.get(route)[0] += travelTime; 
        travelMap.get(route)[1] += 1;          

    
        checkInMap.remove(id);
    }

    public double getAverageTime(String startStation, String endStation) {
        String route = startStation + "-" + endStation;
        double[] stats = travelMap.get(route);
        return stats[0] / stats[1];
    }

  
    private static class Pair {
        String station;
        int time;

        Pair(String station, int time) {
            this.station = station;
            this.time = time;
        }
    }
}
