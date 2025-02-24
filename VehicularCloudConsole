import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileWriter;
import java.io.IOException;
import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;

public class VehicularCloudConsole extends JFrame {
    private JPanel mainPanel;
    private JButton ownerButton, clientButton, ownerListButton, clientListButton;

    public VehicularCloudConsole() {
        // Set up the main frame
        setTitle("Vehicular Cloud Console");
        setSize(800, 600);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Create the main panel
        mainPanel = new JPanel();
        mainPanel.setLayout(new GridLayout(4, 1));

        // Add buttons to the main panel
        ownerButton = new JButton(" Owner");
        clientButton = new JButton(" Client");
        ownerListButton = new JButton(" Owner List");
        clientListButton = new JButton(" Registered Client");

        mainPanel.add(ownerButton);
        mainPanel.add(clientButton);
        mainPanel.add(ownerListButton);
        mainPanel.add(clientListButton);
        
        Font buttonFont = new Font("Arial", Font.BOLD, 24); 
        ownerButton.setFont(buttonFont);
        clientButton.setFont(buttonFont);
        ownerListButton.setFont(buttonFont);
        clientListButton.setFont(buttonFont);
        
        ownerButton.setBackground(new Color(176, 224, 230)); 
        clientButton.setBackground(new Color(190, 100, 2)); 
        ownerListButton.setBackground(new Color(176, 224, 230)); 
        clientListButton.setBackground(new Color(190, 100, 2)); 
     
        
        // Add action listeners
        ownerButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                openOwnerPage();
            }
        });

        clientButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                openClientPage();
            }
        });

        ownerListButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                displayOwnerList();
            }
        });

        clientListButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                displayClientList();
            }
        });

        // Add the main panel to the frame
        add(mainPanel);
    }

    private void openOwnerPage() {
        JFrame ownerFrame = new JFrame("Owner Registration");
        ownerFrame.setSize(800, 600);
        ownerFrame.setLocationRelativeTo(null);
        


        JPanel ownerPanel = new JPanel();
        ownerPanel.setLayout(new GridLayout(5, 2));
       

        JLabel ownerIdLabel = new JLabel("Owner ID:(****-****)");
        JTextField ownerIdField = new JTextField();
        JLabel ownerContactLabel = new JLabel("Owner Contact Info:(number)");
        JTextField ownerContactField = new JTextField();
        JLabel vehicleInfoLabel = new JLabel("Vehicle Information:");
        JTextField vehicleInfoField = new JTextField();
        JLabel residencyTimeLabel = new JLabel("Residency Time (hours):");
        JTextField residencyTimeField = new JTextField();
        JButton submitButton = new JButton("Submit");

        ownerPanel.add(ownerIdLabel);
        ownerPanel.add(ownerIdField);
        ownerPanel.add(vehicleInfoLabel);
        ownerPanel.add(vehicleInfoField);
        ownerPanel.add(residencyTimeLabel);
        ownerPanel.add(residencyTimeField);
        ownerPanel.add(ownerContactLabel);
        ownerPanel.add(ownerContactField);
        ownerPanel.add(submitButton);
  

        submitButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
         String ownerId = ownerIdField.getText();
         String vehicleInfo = vehicleInfoField.getText();
         String residencyTime = residencyTimeField.getText();
         String ownerContact = ownerContactField.getText();
            
                if (ownerId.isEmpty() || vehicleInfo.isEmpty() || residencyTime.isEmpty() || ownerContact.isEmpty()) {
                    JOptionPane.showMessageDialog(null, "All fields are required!");
                } else {
                    saveOwnerInfo(ownerId, vehicleInfo, residencyTime,ownerContact );
                    JOptionPane.showMessageDialog(null, "Owner information saved!");
                    ownerFrame.dispose();
                }
            }
        });

        ownerFrame.add(ownerPanel);
        ownerFrame.setVisible(true);
    }

    private void openClientPage() {
        JFrame clientFrame = new JFrame("Client Registration");
        clientFrame.setSize(800, 600);
        clientFrame.setLocationRelativeTo(null);

        JPanel clientPanel = new JPanel();
        clientPanel.setLayout(new GridLayout(5, 2));

        JLabel clientIdLabel = new JLabel("Client ID:(***-***)");
        JTextField clientIdField = new JTextField();
        JLabel clientContactLabel = new JLabel("Client Contact Info:(number)");
        JTextField clientContactField = new JTextField();
        JLabel jobDurationLabel = new JLabel("Job Duration (hours):");
        JTextField jobDurationField = new JTextField();
        JLabel jobDeadlineLabel = new JLabel("Job Deadline (YYYY-MM-DD):");
        JTextField jobDeadlineField = new JTextField();
        JButton submitButton = new JButton("Submit");

        clientPanel.add(clientIdLabel);
        clientPanel.add(clientIdField);
        clientPanel.add(jobDurationLabel);
        clientPanel.add(jobDurationField);
        clientPanel.add(jobDeadlineLabel);
        clientPanel.add(jobDeadlineField);
        clientPanel.add(clientContactLabel);
        clientPanel.add(clientContactField);
        clientPanel.add(submitButton);

        submitButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
         String clientId = clientIdField.getText();
         String jobDuration = jobDurationField.getText();
         String jobDeadline = jobDeadlineField.getText();
         String clientContact = clientContactField.getText();
                if (clientId.isEmpty() || jobDuration.isEmpty() || jobDeadline.isEmpty() ||clientContact.isEmpty() ) {
                    JOptionPane.showMessageDialog(null, "All fields are required!");
                } else {
                    saveClientInfo(clientId, jobDuration, jobDeadline, clientContact);
                    JOptionPane.showMessageDialog(null, "Client information saved!");
                    clientFrame.dispose();
                }
            }
        });

        clientFrame.add(clientPanel);
        clientFrame.setVisible(true);
    }

    private void saveOwnerInfo(String ownerId, String vehicleInfo, String residencyTime,String ownerContact) {
        String timestamp = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date());
        String data = String.format("Owner ID: %s, Vehicle Info: %s, Residency Time: %s, ownerContact: %s,Timestamp: %s%n",
                ownerId, vehicleInfo, residencyTime, ownerContact, timestamp);

        try (FileWriter writer = new FileWriter("owners.txt", true)) {
            writer.write(data);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private void saveClientInfo(String clientId, String jobDuration, String jobDeadline, String clientContact) {
        String timestamp = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date());
        String data = String.format("Client ID: %s, Job Duration: %s, Job Deadline: %s, clientContact: %s, Timestamp: %s%n",
                clientId, jobDuration, jobDeadline,clientContact, timestamp);

        try (FileWriter writer = new FileWriter("clients.txt", true)) {
            writer.write(data);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    private void displayOwnerList() {
        JFrame ownerListFrame = new JFrame("Owner List");
        ownerListFrame.setSize(800, 600);
        ownerListFrame.setLocationRelativeTo(null);

        JTextArea textArea = new JTextArea();
        textArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(textArea);

        try {
            File file = new File("owners.txt");
            Scanner scanner = new Scanner(file);
            while (scanner.hasNextLine()) {
                textArea.append(scanner.nextLine() + "\n");
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            textArea.setText("No owner data found.");
        }

        ownerListFrame.add(scrollPane);
        ownerListFrame.setVisible(true);
    }

    private void displayClientList() {
        JFrame clientListFrame = new JFrame("Registered Client List");
        clientListFrame.setSize(800, 600);
        clientListFrame.setLocationRelativeTo(null);

        JTextArea textArea = new JTextArea();
        textArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(textArea);

        try {
            File file = new File("clients.txt");
            Scanner scanner = new Scanner(file);
            while (scanner.hasNextLine()) {
                textArea.append(scanner.nextLine() + "\n");
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            textArea.setText("No client data found.");
        }

        clientListFrame.add(scrollPane);
        clientListFrame.setVisible(true);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                new VehicularCloudConsole().setVisible(true);
            }
        });
    }
}
