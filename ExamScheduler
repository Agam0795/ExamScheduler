import java.util.*;

public class ExamScheduler 
{

        private static final int VERTICES = 15;
        private static final int DAYS = 10;

        private static int[][] graph = new int[VERTICES + 1][VERTICES + 1];

        private static int[] dayAssigned = new int[VERTICES + 1];

        public static void main(String[] args) 
        {
            initializeGraph();
            assignDays();
            printSchedule();
        }

        private static void initializeGraph() 
        {
            for (int i = 1; i <= VERTICES; i++) 
            {
                for (int j = 1; j <= VERTICES; j++)
                {
                    graph[i][j] = 0;
                }
            }
            addEdge(1, 2);
            addEdge(1, 3);
            addEdge(1, 4);
            addEdge(1, 5);
            addEdge(1, 6);
            addEdge(1, 7);
            addEdge(1, 9);
            addEdge(1, 10);

            addEdge(2, 1);
            addEdge(2, 3);
            addEdge(2, 4);
            addEdge(2, 6);
            addEdge(2, 9);
            addEdge(2, 10);
            addEdge(2, 11);
            addEdge(2, 12);
            addEdge(2, 14);
            addEdge(2, 15);

            addEdge(3, 1);
            addEdge(3, 2);
            addEdge(3, 4);
            addEdge(3, 11);
            addEdge(3, 14);
            addEdge(3, 15);

            addEdge(4, 1);
            addEdge(4, 3);
            addEdge(4, 5);
            addEdge(4, 6);
            addEdge(4, 7);
            addEdge(4, 9);
            addEdge(4, 10);

            addEdge(5, 1);
            addEdge(5, 4);
            addEdge(5, 7);
            addEdge(5, 8);
            addEdge(5, 9);
            addEdge(5, 10);
            addEdge(5, 13);
            addEdge(5, 14);

            addEdge(6, 1);
            addEdge(6, 2);
            addEdge(6, 4);
            addEdge(6, 7);
            addEdge(6, 8);
            addEdge(6, 9);
            addEdge(6, 10);
            addEdge(6, 12);
            addEdge(6, 13);

            addEdge(7, 1);
            addEdge(7, 4);
            addEdge(7, 5);
            addEdge(7, 6);
            addEdge(7, 8);
            addEdge(7, 9);
            addEdge(7, 10);
            addEdge(7, 12);
            addEdge(7, 13);

            addEdge(8, 5);
            addEdge(8, 6);
            addEdge(8, 7);
            addEdge(8, 9);
            addEdge(8, 10);

            addEdge(9, 1);
            addEdge(9, 2);
            addEdge(9, 4);
            addEdge(9, 5);
            addEdge(9, 6);
            addEdge(9, 7);
            addEdge(9, 8);
            addEdge(9, 10);
            addEdge(9, 12);

            addEdge(10, 1);
            addEdge(10, 2);
            addEdge(10, 4);
            addEdge(10, 5);
            addEdge(10, 6);
            addEdge(10, 7);
            addEdge(10, 8);
            addEdge(10, 9);
            addEdge(10, 12);

            addEdge(11, 2);
            addEdge(11, 3);
            addEdge(11, 12);

            addEdge(12, 3);
            addEdge(12, 6);
            addEdge(12, 7);
            addEdge(12, 9);
            addEdge(12, 10);
            addEdge(12, 11);
            addEdge(12, 13);

            addEdge(13, 5);
            addEdge(13, 6);
            addEdge(13, 7);
            addEdge(13, 12);

            addEdge(14, 2);
            addEdge(14, 3);
            addEdge(14, 5);

            addEdge(15, 2);
            addEdge(15, 3);

        }

        private static void addEdge(int u, int v) 
        {
            graph[u][v] = 1;
            graph[v][u] = 1;
        }

        private static void assignDays() 
        {
            Arrays.fill(dayAssigned, -1);

            int[] examCount = new int[DAYS];

            dayAssigned[1] = 0;
            examCount[0]++;
 
            boolean[] availableDays = new boolean[DAYS];

            for (int u = 2; u <= VERTICES; u++) 
            {

                Arrays.fill(availableDays, true);
                for (int i = 1; i <= VERTICES; i++) 
                {
                    if (graph[u][i] == 1 && dayAssigned[i] != -1) 
                    {
                        availableDays[dayAssigned[i]] = false;
                    }
                }

                int day = -1;
                for (int i = 0; i < DAYS; i++) 
                {
                    if (availableDays[i] && examCount[i] < 3)
                    {
                        day = i;
                        break;
                    }
                }

                if (day != -1) 
                {
                    dayAssigned[u] = day;
                    examCount[day]++;
                } 
                else 
                {
                    System.err.println("Unable to assign a day to vertex " + u);
                }
            }

            for (int i = 1; i <= VERTICES; i++) 
            {
                if (dayAssigned[i] == -1) 
                {
                    System.err.println("Vertex " + i + " was not assigned a valid day.");
                }
            }
        }

    private static void printSchedule() 
    {

        int[][] schedule = new int[DAYS][VERTICES];

        int[] countPerDay = new int[DAYS];

        for (int i = 1; i <= VERTICES; i++) 
        {
            int day = dayAssigned[i];
            if (day != -1) 
            { 
                schedule[day][countPerDay[day]++] = i;
            }
        }

        System.out.println("Exam Schedule:");
        for (int i = 0; i < DAYS; i++) 
        {
            System.out.print("Day " + (i + 1) + ": ");
            for (int j = 0; j < countPerDay[i]; j++) 
            {
                System.out.print("V" + schedule[i][j] + " ");
            }
            System.out.println();
        }

        }
}
