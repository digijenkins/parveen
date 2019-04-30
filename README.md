package com.POMtest;

import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class PraveenTest {

	public static void main(String[] args) {
		String FILENAME = "/home/digismart/parveen1.txt";
		String[] paymentType = { "Paytm", "Upi" };
		String qquery = "{ \"transferType\" : \"Paytm\", \"totalAmount\" : 1, \"serviceCharge\" : 0, \"transferAmount\" : 1, \"mobileNo\" : 7093245406, \"upiName\" : \"\", \"upiId\" : \"\", \"userId\" : 61, \"crtLongDate\" : 1547718558030, \"transferStatus\" : 1, \"groupDate\" : \"2019-01-17\", \"ver\" : 3, \"createdDate\" : ISODate(\"2019-01-17T09:49:18.030Z\"), \"modifiedDate\" : ISODate(\"2019-01-17T09:49:18.030Z\")}";
		String date[] = { "2019-01-17", "2019-01-18", "2019-01-19" };
		int[] paymentStatus = { 0, 1, 2, 3 };

		/*
		 * String replace = qquery.replace("\"transferType\" : \"Paytm\"",
		 * "\"transferType\" : \""+paymentType[1]+"\""); System.err.println(replace);
		 */// "transferType" : "Paytm"
			// transferStatus : 0,1,2,3
		/*
		 * String replace2 = query.replace("\"paymentStatus\" : 1",
		 * "\"paymentStatus\" :" + 4); //String replace =
		 * replace2.replace("\"groupDate\" : \"2019-01-17\"","\"groupDate\" : \""+date[2
		 * ]+"\"");
		 * 
		 */
		BufferedWriter bw = null;
		FileWriter fw = null;
		StringBuilder saving = new StringBuilder();
		for (int p = 0; p < paymentType.length; p++) {
			for (int i = 0; i < date.length; i++) {

				for (int k = 0; k < paymentStatus.length; k++) {
					String replace = qquery.replace("\"transferStatus\" : 1",
							"\"transferStatus\" :" + paymentStatus[k]);
					String replace3 = replace.replace("\"groupDate\" : \"2019-01-17\"",
							"\"groupDate\" : \"" + date[i] + "\"");
					String replace4 = replace3.replace("\"transferType\" : \"Paytm\"",
							"\"transferType\" : \"" + paymentType[p] + "\"");
					System.err.println(replace3);
					for (int l = 0; l < 20000; l++) {

						saving = saving.append(replace4 + "\n");

					}

				}
			}
		}
		try {
			fw = new FileWriter(FILENAME);
		} catch (IOException e) {
			e.printStackTrace();
		}
		bw = new BufferedWriter(fw);
		try {
			bw.write(saving.toString());
		} catch (IOException e) {
			e.printStackTrace();
		} finally {

			try {

				if (bw != null)
					bw.close();

				if (fw != null)
					fw.close();

			} catch (IOException ex) {

				ex.printStackTrace();

			}

		}

		System.err.println("Done!!!" + qquery);
	}

}
