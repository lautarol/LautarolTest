---
title: Stream processing with Azure Stream Analytics
titleSuffix: Azure Reference Architectures
description: Create an end-to-end stream processing pipeline in Azure.
author: MikeWasson
ms.date: 11/06/2018
ms.topic: reference-architecture
ms.service: architecture-center
ms.subservice: reference-architecture
ms.custom: seodec18
---

# <a name="create-a-stream-processing-pipeline-with-azure-stream-analytics"></a><span data-ttu-id="2475d-103">Create a stream processing pipeline with Azure Stream Analytics</span><span class="sxs-lookup"><span data-stu-id="2475d-103">Create a stream processing pipeline with Azure Stream Analytics</span></span>

<span data-ttu-id="2475d-104">This reference architecture shows an end-to-end [stream processing](/azure/architecture/data-guide/big-data/real-time-processing) pipeline.</span><span class="sxs-lookup"><span data-stu-id="2475d-104">This reference architecture shows an end-to-end [stream processing](/azure/architecture/data-guide/big-data/real-time-processing) pipeline.</span></span> <span data-ttu-id="2475d-105">The pipeline ingests data from two sources, correlates records in the two streams, and calculates a rolling average across a time window.</span><span class="sxs-lookup"><span data-stu-id="2475d-105">The pipeline ingests data from two sources, correlates records in the two streams, and calculates a rolling average across a time window.</span></span> <span data-ttu-id="2475d-106">The results are stored for further analysis.</span><span class="sxs-lookup"><span data-stu-id="2475d-106">The results are stored for further analysis.</span></span>

<span data-ttu-id="2475d-107">A reference implementation for this architecture is available on [GitHub][github].</span><span class="sxs-lookup"><span data-stu-id="2475d-107">A reference implementation for this architecture is available on [GitHub][github].</span></span>

![Reference architecture for creating a stream processing pipeline with Azure Stream Analytics](./images/stream-processing-asa/stream-processing-asa.png)

<span data-ttu-id="2475d-109">**Scenario**: A taxi company collects data about each taxi trip.</span><span class="sxs-lookup"><span data-stu-id="2475d-109">**Scenario**: A taxi company collects data about each taxi trip.</span></span> <span data-ttu-id="2475d-110">For this scenario, we assume there are two separate devices sending data.</span><span class="sxs-lookup"><span data-stu-id="2475d-110">For this scenario, we assume there are two separate devices sending data.</span></span> <span data-ttu-id="2475d-111">The taxi has a meter that sends information about each ride &mdash; the duration, distance, and pickup and dropoff locations.</span><span class="sxs-lookup"><span data-stu-id="2475d-111">The taxi has a meter that sends information about each ride &mdash; the duration, distance, and pickup and dropoff locations.</span></span> <span data-ttu-id="2475d-112">A separate device accepts payments from customers and sends data about fares.</span><span class="sxs-lookup"><span data-stu-id="2475d-112">A separate device accepts payments from customers and sends data about fares.</span></span> <span data-ttu-id="2475d-113">The taxi company wants to calculate the average tip per mile driven, in real time, in order to spot trends.</span><span class="sxs-lookup"><span data-stu-id="2475d-113">The taxi company wants to calculate the average tip per mile driven, in real time, in order to spot trends.</span></span>

## <a name="architecture"></a><span data-ttu-id="2475d-114">Architecture</span><span class="sxs-lookup"><span data-stu-id="2475d-114">Architecture</span></span>

<span data-ttu-id="2475d-115">The architecture consists of the following components.</span><span class="sxs-lookup"><span data-stu-id="2475d-115">The architecture consists of the following components.</span></span>

<span data-ttu-id="2475d-116">**Data sources**.</span><span class="sxs-lookup"><span data-stu-id="2475d-116">**Data sources**.</span></span> <span data-ttu-id="2475d-117">In this architecture, there are two data sources that generate data streams in real time.</span><span class="sxs-lookup"><span data-stu-id="2475d-117">In this architecture, there are two data sources that generate data streams in real time.</span></span> <span data-ttu-id="2475d-118">The first stream contains ride information, and the second contains fare information.</span><span class="sxs-lookup"><span data-stu-id="2475d-118">The first stream contains ride information, and the second contains fare information.</span></span> <span data-ttu-id="2475d-119">The reference architecture includes a simulated data generator that reads from a set of static files and pushes the data to Event Hubs.</span><span class="sxs-lookup"><span data-stu-id="2475d-119">The reference architecture includes a simulated data generator that reads from a set of static files and pushes the data to Event Hubs.</span></span> <span data-ttu-id="2475d-120">In a real application, the data sources would be devices installed in the taxi cabs.</span><span class="sxs-lookup"><span data-stu-id="2475d-120">In a real application, the data sources would be devices installed in the taxi cabs.</span></span>

<span data-ttu-id="2475d-121">**Azure Event Hubs**.</span><span class="sxs-lookup"><span data-stu-id="2475d-121">**Azure Event Hubs**.</span></span> <span data-ttu-id="2475d-122">[Event Hubs](/azure/event-hubs/) is an event ingestion service.</span><span class="sxs-lookup"><span data-stu-id="2475d-122">[Event Hubs](/azure/event-hubs/) is an event ingestion service.</span></span> <span data-ttu-id="2475d-123">This architecture uses two event hub instances, one for each data source.</span><span class="sxs-lookup"><span data-stu-id="2475d-123">This architecture uses two event hub instances, one for each data source.</span></span> <span data-ttu-id="2475d-124">Each data source sends a stream of data to the associated event hub.</span><span class="sxs-lookup"><span data-stu-id="2475d-124">Each data source sends a stream of data to the associated event hub.</span></span>

<span data-ttu-id="2475d-125">**Azure Stream Analytics**.</span><span class="sxs-lookup"><span data-stu-id="2475d-125">**Azure Stream Analytics**.</span></span> <span data-ttu-id="2475d-126">[Stream Analytics](/azure/stream-analytics/) is an event-processing engine.</span><span class="sxs-lookup"><span data-stu-id="2475d-126">[Stream Analytics](/azure/stream-analytics/) is an event-processing engine.</span></span> <span data-ttu-id="2475d-127">A Stream Analytics job reads the data streams from the two event hubs and performs stream processing.</span><span class="sxs-lookup"><span data-stu-id="2475d-127">A Stream Analytics job reads the data streams from the two event hubs and performs stream processing.</span></span>

<span data-ttu-id="2475d-128">**Cosmos DB**.</span><span class="sxs-lookup"><span data-stu-id="2475d-128">**Cosmos DB**.</span></span> <span data-ttu-id="2475d-129">The output from the Stream Analytics job is a series of records, which are written as JSON documents to a Cosmos DB document database.</span><span class="sxs-lookup"><span data-stu-id="2475d-129">The output from the Stream Analytics job is a series of records, which are written as JSON documents to a Cosmos DB document database.</span></span>

<span data-ttu-id="2475d-130">**Microsoft Power BI**.</span><span class="sxs-lookup"><span data-stu-id="2475d-130">**Microsoft Power BI**.</span></span> <span data-ttu-id="2475d-131">Power BI is a suite of business analytics tools to analyze data for business insights.</span><span class="sxs-lookup"><span data-stu-id="2475d-131">Power BI is a suite of business analytics tools to analyze data for business insights.</span></span> <span data-ttu-id="2475d-132">In this architecture, it loads the data from Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2475d-132">In this architecture, it loads the data from Cosmos DB.</span></span> <span data-ttu-id="2475d-133">This allows users to analyze the complete set of historical data that's been collected.</span><span class="sxs-lookup"><span data-stu-id="2475d-133">This allows users to analyze the complete set of historical data that's been collected.</span></span> <span data-ttu-id="2475d-134">You could also stream the results directly from Stream Analytics to Power BI for a real-time view of the data.</span><span class="sxs-lookup"><span data-stu-id="2475d-134">You could also stream the results directly from Stream Analytics to Power BI for a real-time view of the data.</span></span> <span data-ttu-id="2475d-135">For more information, see [Real-time streaming in Power BI](/power-bi/service-real-time-streaming).</span><span class="sxs-lookup"><span data-stu-id="2475d-135">For more information, see [Real-time streaming in Power BI](/power-bi/service-real-time-streaming).</span></span>

<span data-ttu-id="2475d-136">**Azure Monitor**.</span><span class="sxs-lookup"><span data-stu-id="2475d-136">**Azure Monitor**.</span></span> <span data-ttu-id="2475d-137">[Azure Monitor](/azure/monitoring-and-diagnostics/) collects performance metrics about the Azure services deployed in the solution.</span><span class="sxs-lookup"><span data-stu-id="2475d-137">[Azure Monitor](/azure/monitoring-and-diagnostics/) collects performance metrics about the Azure services deployed in the solution.</span></span> <span data-ttu-id="2475d-138">By visualizing these in a dashboard, you can get insights into the health of the solution.</span><span class="sxs-lookup"><span data-stu-id="2475d-138">By visualizing these in a dashboard, you can get insights into the health of the solution.</span></span>

## <a name="data-ingestion"></a><span data-ttu-id="2475d-139">Data ingestion</span><span class="sxs-lookup"><span data-stu-id="2475d-139">Data ingestion</span></span>

<!-- markdownlint-disable MD033 -->

<span data-ttu-id="2475d-140">To simulate a data source, this reference architecture uses the [New York City Taxi Data](https://uofi.app.box.com/v/NYCtaxidata/folder/2332218797) dataset<sup>[[1]](#note1)</sup>.</span><span class="sxs-lookup"><span data-stu-id="2475d-140">To simulate a data source, this reference architecture uses the [New York City Taxi Data](https://uofi.app.box.com/v/NYCtaxidata/folder/2332218797) dataset<sup>[[1]](#note1)</sup>.</span></span> <span data-ttu-id="2475d-141">This dataset contains data about taxi trips in New York City over a 4-year period (2010 &ndash; 2013).</span><span class="sxs-lookup"><span data-stu-id="2475d-141">This dataset contains data about taxi trips in New York City over a 4-year period (2010 &ndash; 2013).</span></span> <span data-ttu-id="2475d-142">It contains two types of record: Ride data and fare data.</span><span class="sxs-lookup"><span data-stu-id="2475d-142">It contains two types of record: Ride data and fare data.</span></span> <span data-ttu-id="2475d-143">Ride data includes trip duration, trip distance, and pickup and dropoff location.</span><span class="sxs-lookup"><span data-stu-id="2475d-143">Ride data includes trip duration, trip distance, and pickup and dropoff location.</span></span> <span data-ttu-id="2475d-144">Fare data includes fare, tax, and tip amounts.</span><span class="sxs-lookup"><span data-stu-id="2475d-144">Fare data includes fare, tax, and tip amounts.</span></span> <span data-ttu-id="2475d-145">Common fields in both record types include medallion number, hack license, and vendor ID.</span><span class="sxs-lookup"><span data-stu-id="2475d-145">Common fields in both record types include medallion number, hack license, and vendor ID.</span></span> <span data-ttu-id="2475d-146">Together these three fields uniquely identify a taxi plus a driver.</span><span class="sxs-lookup"><span data-stu-id="2475d-146">Together these three fields uniquely identify a taxi plus a driver.</span></span> <span data-ttu-id="2475d-147">The data is stored in CSV format.</span><span class="sxs-lookup"><span data-stu-id="2475d-147">The data is stored in CSV format.</span></span>

<span data-ttu-id="2475d-148">[1]<span id="note1"> Donovan, Brian; Work, Dan (2016): New York City Taxi Trip Data (2010-2013).</span><span class="sxs-lookup"><span data-stu-id="2475d-148">[1]<span id="note1"> Donovan, Brian; Work, Dan (2016): New York City Taxi Trip Data (2010-2013).</span></span> <span data-ttu-id="2475d-149">University of Illinois at Urbana-Champaign.</span><span class="sxs-lookup"><span data-stu-id="2475d-149">University of Illinois at Urbana-Champaign.</span></span> <https://doi.org/10.13012/J8PN93H8>

<!-- markdownlint-enable MD033 -->

<span data-ttu-id="2475d-150">The data generator is a .NET Core application that reads the records and sends them to Azure Event Hubs.</span><span class="sxs-lookup"><span data-stu-id="2475d-150">The data generator is a .NET Core application that reads the records and sends them to Azure Event Hubs.</span></span> <span data-ttu-id="2475d-151">The generator sends ride data in JSON format and fare data in CSV format.</span><span class="sxs-lookup"><span data-stu-id="2475d-151">The generator sends ride data in JSON format and fare data in CSV format.</span></span>

<span data-ttu-id="2475d-152">Event Hubs uses [partitions](/azure/event-hubs/event-hubs-features#partitions) to segment the data.</span><span class="sxs-lookup"><span data-stu-id="2475d-152">Event Hubs uses [partitions](/azure/event-hubs/event-hubs-features#partitions) to segment the data.</span></span> <span data-ttu-id="2475d-153">Partitions allow a consumer to read each partition in parallel.</span><span class="sxs-lookup"><span data-stu-id="2475d-153">Partitions allow a consumer to read each partition in parallel.</span></span> <span data-ttu-id="2475d-154">When you send data to Event Hubs, you can specify the partition key explicitly.</span><span class="sxs-lookup"><span data-stu-id="2475d-154">When you send data to Event Hubs, you can specify the partition key explicitly.</span></span> <span data-ttu-id="2475d-155">Otherwise, records are assigned to partitions in round-robin fashion.</span><span class="sxs-lookup"><span data-stu-id="2475d-155">Otherwise, records are assigned to partitions in round-robin fashion.</span></span>

<span data-ttu-id="2475d-156">In this particular scenario, ride data and fare data should end up with the same partition ID for a given taxi cab.</span><span class="sxs-lookup"><span data-stu-id="2475d-156">In this particular scenario, ride data and fare data should end up with the same partition ID for a given taxi cab.</span></span> <span data-ttu-id="2475d-157">This enables Stream Analytics to apply a degree of parallelism when it correlates the two streams.</span><span class="sxs-lookup"><span data-stu-id="2475d-157">This enables Stream Analytics to apply a degree of parallelism when it correlates the two streams.</span></span> <span data-ttu-id="2475d-158">A record in partition *n* of the ride data will match a record in partition *n* of the fare data.</span><span class="sxs-lookup"><span data-stu-id="2475d-158">A record in partition *n* of the ride data will match a record in partition *n* of the fare data.</span></span>

![Diagram of stream processing with Azure Stream Analytics and Event Hubs](./images/stream-processing-asa/stream-processing-eh.png)

<span data-ttu-id="2475d-160">In the data generator, the common data model for both record types has a `PartitionKey` property which is the concatenation of `Medallion`, `HackLicense`, and `VendorId`.</span><span class="sxs-lookup"><span data-stu-id="2475d-160">In the data generator, the common data model for both record types has a `PartitionKey` property which is the concatenation of `Medallion`, `HackLicense`, and `VendorId`.</span></span>

```csharp
public abstract class TaxiData
{
    public TaxiData()
    {
    }

    [JsonProperty]
    public long Medallion { get; set; }

    [JsonProperty]
    public long HackLicense { get; set; }

    [JsonProperty]
    public string VendorId { get; set; }

    [JsonProperty]
    public DateTimeOffset PickupTime { get; set; }

    [JsonIgnore]
    public string PartitionKey
    {
        get => $"{Medallion}_{HackLicense}_{VendorId}";
    }
```

<span data-ttu-id="2475d-161">This property is used to provide an explicit partition key when sending to Event Hubs:</span><span class="sxs-lookup"><span data-stu-id="2475d-161">This property is used to provide an explicit partition key when sending to Event Hubs:</span></span>

```csharp
using (var client = pool.GetObject())
{
    return client.Value.SendAsync(new EventData(Encoding.UTF8.GetBytes(
        t.GetData(dataFormat))), t.PartitionKey);
}
```

## <a name="stream-processing"></a><span data-ttu-id="2475d-162">Stream processing</span><span class="sxs-lookup"><span data-stu-id="2475d-162">Stream processing</span></span>

<span data-ttu-id="2475d-163">The stream processing job is defined using a SQL query with several distinct steps.</span><span class="sxs-lookup"><span data-stu-id="2475d-163">The stream processing job is defined using a SQL query with several distinct steps.</span></span> <span data-ttu-id="2475d-164">The first two steps simply select records from the two input streams.</span><span class="sxs-lookup"><span data-stu-id="2475d-164">The first two steps simply select records from the two input streams.</span></span>

```sql
WITH
Step1 AS (
    SELECT PartitionId,
           TRY_CAST(Medallion AS nvarchar(max)) AS Medallion,
           TRY_CAST(HackLicense AS nvarchar(max)) AS HackLicense,
           VendorId,
           TRY_CAST(PickupTime AS datetime) AS PickupTime,
           TripDistanceInMiles
    FROM [TaxiRide] PARTITION BY PartitionId
),
Step2 AS (
    SELECT PartitionId,
           medallion AS Medallion,
           hack_license AS HackLicense,
           vendor_id AS VendorId,
           TRY_CAST(pickup_datetime AS datetime) AS PickupTime,
           tip_amount AS TipAmount
    FROM [TaxiFare] PARTITION BY PartitionId
),
```

<span data-ttu-id="2475d-165">The next step joins the two input streams to select matching records from each stream.</span><span class="sxs-lookup"><span data-stu-id="2475d-165">The next step joins the two input streams to select matching records from each stream.</span></span>

```sql
Step3 AS (
  SELECT
         tr.Medallion,
         tr.HackLicense,
         tr.VendorId,
         tr.PickupTime,
         tr.TripDistanceInMiles,
         tf.TipAmount
    FROM [Step1] tr
    PARTITION BY PartitionId
    JOIN [Step2] tf PARTITION BY PartitionId
      ON tr.Medallion = tf.Medallion
     AND tr.HackLicense = tf.HackLicense
     AND tr.VendorId = tf.VendorId
     AND tr.PickupTime = tf.PickupTime
     AND tr.PartitionId = tf.PartitionId
     AND DATEDIFF(minute, tr, tf) BETWEEN 0 AND 15
)
```

<span data-ttu-id="2475d-166">This query joins records on a set of fields that uniquely identify matching records (Medallion, HackLicense, VendorId, and PickupTime).</span><span class="sxs-lookup"><span data-stu-id="2475d-166">This query joins records on a set of fields that uniquely identify matching records (Medallion, HackLicense, VendorId, and PickupTime).</span></span> <span data-ttu-id="2475d-167">The `JOIN` statement also includes the partition ID.</span><span class="sxs-lookup"><span data-stu-id="2475d-167">The `JOIN` statement also includes the partition ID.</span></span> <span data-ttu-id="2475d-168">As mentioned, this takes advantage of the fact that matching records always have the same partition ID in this scenario.</span><span class="sxs-lookup"><span data-stu-id="2475d-168">As mentioned, this takes advantage of the fact that matching records always have the same partition ID in this scenario.</span></span>

<span data-ttu-id="2475d-169">In Stream Analytics, joins are *temporal*, meaning records are joined within a particular window of time.</span><span class="sxs-lookup"><span data-stu-id="2475d-169">In Stream Analytics, joins are *temporal*, meaning records are joined within a particular window of time.</span></span> <span data-ttu-id="2475d-170">Otherwise, the job might need to wait indefinitely for a match.</span><span class="sxs-lookup"><span data-stu-id="2475d-170">Otherwise, the job might need to wait indefinitely for a match.</span></span> <span data-ttu-id="2475d-171">The [DATEDIFF](https://msdn.microsoft.com/azure/stream-analytics/reference/join-azure-stream-analytics) function specifies how far two matching records can be separated in time for a match.</span><span class="sxs-lookup"><span data-stu-id="2475d-171">The [DATEDIFF](https://msdn.microsoft.com/azure/stream-analytics/reference/join-azure-stream-analytics) function specifies how far two matching records can be separated in time for a match.</span></span>

<span data-ttu-id="2475d-172">The last step in the job computes the average tip per mile, grouped by a hopping window of 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="2475d-172">The last step in the job computes the average tip per mile, grouped by a hopping window of 5 minutes.</span></span>

```sql
SELECT System.Timestamp AS WindowTime,
       SUM(tr.TipAmount) / SUM(tr.TripDistanceInMiles) AS AverageTipPerMile
  INTO [TaxiDrain]
  FROM [Step3] tr
  GROUP BY HoppingWindow(Duration(minute, 5), Hop(minute, 1))
```

<span data-ttu-id="2475d-173">Stream Analytics provides several [windowing functions](/azure/stream-analytics/stream-analytics-window-functions).</span><span class="sxs-lookup"><span data-stu-id="2475d-173">Stream Analytics provides several [windowing functions](/azure/stream-analytics/stream-analytics-window-functions).</span></span> <span data-ttu-id="2475d-174">A hopping window moves forward in time by a fixed period, in this case 1 minute per hop.</span><span class="sxs-lookup"><span data-stu-id="2475d-174">A hopping window moves forward in time by a fixed period, in this case 1 minute per hop.</span></span> <span data-ttu-id="2475d-175">The result is to calculate a moving average over the past 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="2475d-175">The result is to calculate a moving average over the past 5 minutes.</span></span>

<span data-ttu-id="2475d-176">In the architecture shown here, only the results of the Stream Analytics job are saved to Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="2475d-176">In the architecture shown here, only the results of the Stream Analytics job are saved to Cosmos DB.</span></span> <span data-ttu-id="2475d-177">For a big data scenario, consider also using [Event Hubs Capture](/azure/event-hubs/event-hubs-capture-overview) to save the raw event data into Azure Blob storage.</span><span class="sxs-lookup"><span data-stu-id="2475d-177">For a big data scenario, consider also using [Event Hubs Capture](/azure/event-hubs/event-hubs-capture-overview) to save the raw event data into Azure Blob storage.</span></span> <span data-ttu-id="2475d-178">Keeping the raw data will allow you to run batch queries over your historical data at later time, in order to derive new insights from the data.</span><span class="sxs-lookup"><span data-stu-id="2475d-178">Keeping the raw data will allow you to run batch queries over your historical data at later time, in order to derive new insights from the data.</span></span>

## <a name="scalability-considerations"></a><span data-ttu-id="2475d-179">Scalability considerations</span><span class="sxs-lookup"><span data-stu-id="2475d-179">Scalability considerations</span></span>

### <a name="event-hubs"></a><span data-ttu-id="2475d-180">Event Hubs</span><span class="sxs-lookup"><span data-stu-id="2475d-180">Event Hubs</span></span>

<span data-ttu-id="2475d-181">The throughput capacity of Event Hubs is measured in [throughput units](/azure/event-hubs/event-hubs-features#throughput-units).</span><span class="sxs-lookup"><span data-stu-id="2475d-181">The throughput capacity of Event Hubs is measured in [throughput units](/azure/event-hubs/event-hubs-features#throughput-units).</span></span> <span data-ttu-id="2475d-182">You can autoscale an event hub by enabling [auto-inflate](/azure/event-hubs/event-hubs-auto-inflate), which automatically scales the throughput units based on traffic, up to a configured maximum.</span><span class="sxs-lookup"><span data-stu-id="2475d-182">You can autoscale an event hub by enabling [auto-inflate](/azure/event-hubs/event-hubs-auto-inflate), which automatically scales the throughput units based on traffic, up to a configured maximum.</span></span>

### <a name="stream-analytics"></a><span data-ttu-id="2475d-183">Stream Analytics</span><span class="sxs-lookup"><span data-stu-id="2475d-183">Stream Analytics</span></span>

<span data-ttu-id="2475d-184">For Stream Analytics, the computing resources allocated to a job are measured in Streaming Units.</span><span class="sxs-lookup"><span data-stu-id="2475d-184">For Stream Analytics, the computing resources allocated to a job are measured in Streaming Units.</span></span> <span data-ttu-id="2475d-185">Stream Analytics jobs scale best if the job can be parallelized.</span><span class="sxs-lookup"><span data-stu-id="2475d-185">Stream Analytics jobs scale best if the job can be parallelized.</span></span> <span data-ttu-id="2475d-186">That way, Stream Analytics can distribute the job across multiple compute nodes.</span><span class="sxs-lookup"><span data-stu-id="2475d-186">That way, Stream Analytics can distribute the job across multiple compute nodes.</span></span>

<span data-ttu-id="2475d-187">For Event Hubs input, use the `PARTITION BY` keyword to partition the Stream Analytics job.</span><span class="sxs-lookup"><span data-stu-id="2475d-187">For Event Hubs input, use the `PARTITION BY` keyword to partition the Stream Analytics job.</span></span> <span data-ttu-id="2475d-188">The data will be divided into subsets based on the Event Hubs partitions.</span><span class="sxs-lookup"><span data-stu-id="2475d-188">The data will be divided into subsets based on the Event Hubs partitions.</span></span>

<span data-ttu-id="2475d-189">Windowing functions and temporal joins require additional SU.</span><span class="sxs-lookup"><span data-stu-id="2475d-189">Windowing functions and temporal joins require additional SU.</span></span> <span data-ttu-id="2475d-190">When possible, use `PARTITION BY` so that each partition is processed separately.</span><span class="sxs-lookup"><span data-stu-id="2475d-190">When possible, use `PARTITION BY` so that each partition is processed separately.</span></span> <span data-ttu-id="2475d-191">For more information, see [Understand and adjust Streaming Units](/azure/stream-analytics/stream-analytics-streaming-unit-consumption#windowed-aggregates).</span><span class="sxs-lookup"><span data-stu-id="2475d-191">For more information, see [Understand and adjust Streaming Units](/azure/stream-analytics/stream-analytics-streaming-unit-consumption#windowed-aggregates).</span></span>

<span data-ttu-id="2475d-192">If it's not possible to parallelize the entire Stream Analytics job, try to break the job into multiple steps, starting with one or more parallel steps.</span><span class="sxs-lookup"><span data-stu-id="2475d-192">If it's not possible to parallelize the entire Stream Analytics job, try to break the job into multiple steps, starting with one or more parallel steps.</span></span> <span data-ttu-id="2475d-193">That way, the first steps can run in parallel.</span><span class="sxs-lookup"><span data-stu-id="2475d-193">That way, the first steps can run in parallel.</span></span> <span data-ttu-id="2475d-194">For example, in this reference architecture:</span><span class="sxs-lookup"><span data-stu-id="2475d-194">For example, in this reference architecture:</span></span>

- <span data-ttu-id="2475d-195">Steps 1 and 2 are simple `SELECT` statements that select records within a single partition.</span><span class="sxs-lookup"><span data-stu-id="2475d-195">Steps 1 and 2 are simple `SELECT` statements that select records within a single partition.</span></span>
- <span data-ttu-id="2475d-196">Step 3 performs a partitioned join across two input streams.</span><span class="sxs-lookup"><span data-stu-id="2475d-196">Step 3 performs a partitioned join across two input streams.</span></span> <span data-ttu-id="2475d-197">This step takes advantage of the fact that matching records share the same partition key, and so are guaranteed to have the same partition ID in each input stream.</span><span class="sxs-lookup"><span data-stu-id="2475d-197">This step takes advantage of the fact that matching records share the same partition key, and so are guaranteed to have the same partition ID in each input stream.</span></span>
- <span data-ttu-id="2475d-198">Step 4 aggregates across all of the partitions.</span><span class="sxs-lookup"><span data-stu-id="2475d-198">Step 4 aggregates across all of the partitions.</span></span> <span data-ttu-id="2475d-199">This step cannot be parallelized.</span><span class="sxs-lookup"><span data-stu-id="2475d-199">This step cannot be parallelized.</span></span>

<span data-ttu-id="2475d-200">Use the Stream Analytics [job diagram](/azure/stream-analytics/stream-analytics-job-diagram-with-metrics) to see how many partitions are assigned to each step in the job.</span><span class="sxs-lookup"><span data-stu-id="2475d-200">Use the Stream Analytics [job diagram](/azure/stream-analytics/stream-analytics-job-diagram-with-metrics) to see how many partitions are assigned to each step in the job.</span></span> <span data-ttu-id="2475d-201">The following diagram shows the job diagram for this reference architecture:</span><span class="sxs-lookup"><span data-stu-id="2475d-201">The following diagram shows the job diagram for this reference architecture:</span></span>

![Job diagram](./images/stream-processing-asa/job-diagram.png)

### <a name="cosmos-db"></a><span data-ttu-id="2475d-203">Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2475d-203">Cosmos DB</span></span>

<span data-ttu-id="2475d-204">Throughput capacity for Cosmos DB is measured in [Request Units](/azure/cosmos-db/request-units) (RU).</span><span class="sxs-lookup"><span data-stu-id="2475d-204">Throughput capacity for Cosmos DB is measured in [Request Units](/azure/cosmos-db/request-units) (RU).</span></span> <span data-ttu-id="2475d-205">In order to scale a Cosmos DB container past 10,000 RU, you must specify a [partition key](/azure/cosmos-db/partition-data) when you create the container, and include the partition key in every document.</span><span class="sxs-lookup"><span data-stu-id="2475d-205">In order to scale a Cosmos DB container past 10,000 RU, you must specify a [partition key](/azure/cosmos-db/partition-data) when you create the container, and include the partition key in every document.</span></span>

<span data-ttu-id="2475d-206">In this reference architecture, new documents are created only once per minute (the hopping window interval), so the throughput requirements are quite low.</span><span class="sxs-lookup"><span data-stu-id="2475d-206">In this reference architecture, new documents are created only once per minute (the hopping window interval), so the throughput requirements are quite low.</span></span> <span data-ttu-id="2475d-207">For that reason, there's no need to assign a partition key in this scenario.</span><span class="sxs-lookup"><span data-stu-id="2475d-207">For that reason, there's no need to assign a partition key in this scenario.</span></span>

## <a name="monitoring-considerations"></a><span data-ttu-id="2475d-208">Monitoring considerations</span><span class="sxs-lookup"><span data-stu-id="2475d-208">Monitoring considerations</span></span>

<span data-ttu-id="2475d-209">With any stream processing solution, it's important to monitor the performance and health of the system.</span><span class="sxs-lookup"><span data-stu-id="2475d-209">With any stream processing solution, it's important to monitor the performance and health of the system.</span></span> <span data-ttu-id="2475d-210">[Azure Monitor](/azure/monitoring-and-diagnostics/) collects metrics and diagnostics logs for the Azure services used in the architecture.</span><span class="sxs-lookup"><span data-stu-id="2475d-210">[Azure Monitor](/azure/monitoring-and-diagnostics/) collects metrics and diagnostics logs for the Azure services used in the architecture.</span></span> <span data-ttu-id="2475d-211">Azure Monitor is built into the Azure platform and does not require any additional code in your application.</span><span class="sxs-lookup"><span data-stu-id="2475d-211">Azure Monitor is built into the Azure platform and does not require any additional code in your application.</span></span>

<span data-ttu-id="2475d-212">Any of the following warning signals indicate that you should scale out the relevant Azure resource:</span><span class="sxs-lookup"><span data-stu-id="2475d-212">Any of the following warning signals indicate that you should scale out the relevant Azure resource:</span></span>

- <span data-ttu-id="2475d-213">Event Hubs throttles requests or is close to the daily message quota.</span><span class="sxs-lookup"><span data-stu-id="2475d-213">Event Hubs throttles requests or is close to the daily message quota.</span></span>
- <span data-ttu-id="2475d-214">The Stream Analytics job consistently uses more than 80% of allocated Streaming Units (SU).</span><span class="sxs-lookup"><span data-stu-id="2475d-214">The Stream Analytics job consistently uses more than 80% of allocated Streaming Units (SU).</span></span>
- <span data-ttu-id="2475d-215">Cosmos DB begins to throttle requests.</span><span class="sxs-lookup"><span data-stu-id="2475d-215">Cosmos DB begins to throttle requests.</span></span>

<span data-ttu-id="2475d-216">The reference architecture includes a custom dashboard, which is deployed to the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="2475d-216">The reference architecture includes a custom dashboard, which is deployed to the Azure portal.</span></span> <span data-ttu-id="2475d-217">After you deploy the architecture, you can view the dashboard by opening the [Azure Portal](https://portal.azure.com) and selecting `TaxiRidesDashboard` from list of dashboards.</span><span class="sxs-lookup"><span data-stu-id="2475d-217">After you deploy the architecture, you can view the dashboard by opening the [Azure Portal](https://portal.azure.com) and selecting `TaxiRidesDashboard` from list of dashboards.</span></span> <span data-ttu-id="2475d-218">For more information about creating and deploying custom dashboards in the Azure portal, see [Programmatically create Azure Dashboards](/azure/azure-portal/azure-portal-dashboards-create-programmatically).</span><span class="sxs-lookup"><span data-stu-id="2475d-218">For more information about creating and deploying custom dashboards in the Azure portal, see [Programmatically create Azure Dashboards](/azure/azure-portal/azure-portal-dashboards-create-programmatically).</span></span>

<span data-ttu-id="2475d-219">The following image shows the dashboard after the Stream Analytics job ran for about an hour.</span><span class="sxs-lookup"><span data-stu-id="2475d-219">The following image shows the dashboard after the Stream Analytics job ran for about an hour.</span></span>

![Screenshot of the Taxi Rides dashboard](./images/stream-processing-asa/asa-dashboard.png)

<span data-ttu-id="2475d-221">The panel on the lower left shows that the SU consumption for the Stream Analytics job climbs during the first 15 minutes and then levels off.</span><span class="sxs-lookup"><span data-stu-id="2475d-221">The panel on the lower left shows that the SU consumption for the Stream Analytics job climbs during the first 15 minutes and then levels off.</span></span> <span data-ttu-id="2475d-222">This is a typical pattern as the job reaches a steady state.</span><span class="sxs-lookup"><span data-stu-id="2475d-222">This is a typical pattern as the job reaches a steady state.</span></span>

<span data-ttu-id="2475d-223">Notice that Event Hubs is throttling requests, shown in the upper right panel.</span><span class="sxs-lookup"><span data-stu-id="2475d-223">Notice that Event Hubs is throttling requests, shown in the upper right panel.</span></span> <span data-ttu-id="2475d-224">An occasional throttled request is not a problem, because the Event Hubs client SDK automatically retries when it receives a throttling error.</span><span class="sxs-lookup"><span data-stu-id="2475d-224">An occasional throttled request is not a problem, because the Event Hubs client SDK automatically retries when it receives a throttling error.</span></span> <span data-ttu-id="2475d-225">However, if you see consistent throttling errors, it means the event hub needs more throughput units.</span><span class="sxs-lookup"><span data-stu-id="2475d-225">However, if you see consistent throttling errors, it means the event hub needs more throughput units.</span></span> <span data-ttu-id="2475d-226">The following graph shows a test run using the Event Hubs auto-inflate feature, which automatically scales out the throughput units as needed.</span><span class="sxs-lookup"><span data-stu-id="2475d-226">The following graph shows a test run using the Event Hubs auto-inflate feature, which automatically scales out the throughput units as needed.</span></span>

![Screenshot of Event Hubs autoscaling](./images/stream-processing-asa/stream-processing-eh-autoscale.png)

<span data-ttu-id="2475d-228">Auto-inflate was enabled at about the 06:35 mark.</span><span class="sxs-lookup"><span data-stu-id="2475d-228">Auto-inflate was enabled at about the 06:35 mark.</span></span> <span data-ttu-id="2475d-229">You can see the p drop in throttled requests, as Event Hubs automatically scaled up to 3 throughput units.</span><span class="sxs-lookup"><span data-stu-id="2475d-229">You can see the p drop in throttled requests, as Event Hubs automatically scaled up to 3 throughput units.</span></span>

<span data-ttu-id="2475d-230">Interestingly, this had the side effect of increasing the SU utilization in the Stream Analytics job.</span><span class="sxs-lookup"><span data-stu-id="2475d-230">Interestingly, this had the side effect of increasing the SU utilization in the Stream Analytics job.</span></span> <span data-ttu-id="2475d-231">By throttling, Event Hubs was artificially reducing the ingestion rate for the Stream Analytics job.</span><span class="sxs-lookup"><span data-stu-id="2475d-231">By throttling, Event Hubs was artificially reducing the ingestion rate for the Stream Analytics job.</span></span> <span data-ttu-id="2475d-232">It's actually common that resolving one performance bottleneck reveals another.</span><span class="sxs-lookup"><span data-stu-id="2475d-232">It's actually common that resolving one performance bottleneck reveals another.</span></span> <span data-ttu-id="2475d-233">In this case, allocating additional SU for the Stream Analytics job resolved the issue.</span><span class="sxs-lookup"><span data-stu-id="2475d-233">In this case, allocating additional SU for the Stream Analytics job resolved the issue.</span></span>

## <a name="deploy-the-solution"></a><span data-ttu-id="2475d-234">Deploy the solution</span><span class="sxs-lookup"><span data-stu-id="2475d-234">Deploy the solution</span></span>

<span data-ttu-id="2475d-235">To the deploy and run the reference implementation, follow the steps in the [GitHub readme][github].</span><span class="sxs-lookup"><span data-stu-id="2475d-235">To the deploy and run the reference implementation, follow the steps in the [GitHub readme][github].</span></span>

## <a name="related-resources"></a><span data-ttu-id="2475d-236">Related resources</span><span class="sxs-lookup"><span data-stu-id="2475d-236">Related resources</span></span>

<span data-ttu-id="2475d-237">You may wish to review the following [Azure example scenarios](/azure/architecture/example-scenario) that demonstrate specific solutions using some of the same technologies:</span><span class="sxs-lookup"><span data-stu-id="2475d-237">You may wish to review the following [Azure example scenarios](/azure/architecture/example-scenario) that demonstrate specific solutions using some of the same technologies:</span></span>

- [<span data-ttu-id="2475d-238">IoT and data analytics in the construction industry</span><span class="sxs-lookup"><span data-stu-id="2475d-238">IoT and data analytics in the construction industry</span></span>](/azure/architecture/example-scenario/data/big-data-with-iot)
- [<span data-ttu-id="2475d-239">Real-time fraud detection</span><span class="sxs-lookup"><span data-stu-id="2475d-239">Real-time fraud detection</span></span>](/azure/architecture/example-scenario/data/fraud-detection)

<!-- links -->

[github]: https://github.com/mspnp/azure-stream-analytics-data-pipeline
