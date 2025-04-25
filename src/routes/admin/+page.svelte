<script lang="ts">
  import { firebaseApp } from "$lib/firebase";
  import {
    collection,
    addDoc,
    getFirestore,
    query,
    getDocs,
    deleteDoc,
    doc,
  } from "firebase/firestore";
  import { onMount } from "svelte";

  const db = getFirestore(firebaseApp);
  let loading = false;
  let loadingDelete = false;
  type Video = {
    vimeoId: string;
    title: string;
    description: string;
    id: string;
  };
  let videos: Video[] = [];

  onMount(async () => {
    fetchVideos();
  });

  const fetchVideos = async () => {
    loading = true;
    try {
      const q = query(collection(db, "films"));
      const querySnapshot = await getDocs(q);
      // @ts-ignore
      videos = querySnapshot.docs.map((doc) => ({
        id: doc.id,
        ...doc.data(),
      }));
      console.log("Videos Collection from firebase >>> ", videos);
    } catch (error) {}
    loading = false;
  };

  const onSubmit = async (e: Event) => {
    e.preventDefault();
    loading = true;
    try {
      const form = e.target as HTMLFormElement;
      const videoId = (form.elements.namedItem("videoId") as HTMLInputElement)
        .value;
      const title = (form.elements.namedItem("title") as HTMLInputElement)
        .value;
      const description = (
        form.elements.namedItem("description") as HTMLTextAreaElement
      ).value;

      const docRef = await addDoc(collection(db, "films"), {
        title: title,
        description: description,
        vimeoId: videoId,
      });
      console.log("Document written with ID: ", docRef.id);
    } catch (error) {
      console.error("Error adding document: ", error);
    }
    loading = false;
  };

  const deleteVideo = async (id: string) => {
    loadingDelete = true;
    try {
      const docRef = doc(db, "films", id);
      await deleteDoc(docRef);
      console.log("Document deleted with ID: ", id);
      fetchVideos();
    } catch (error) {
      console.error("Error deleting document: ", error);
    }
    loadingDelete = false;
  };
</script>

<div class="bg-gray-100 min-h-screen p-8">
  <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
    <div class="p-4 border border-gray-400 rounded-lg bg-white shadow-md">
      <h2 class="text-2xl font-semibold">Add Video</h2>
      <p>Add a new video to the collection.</p>
      <form class="mt-4" on:submit={onSubmit}>
        <div class="mb-4">
          <label for="videoId" class="block text-sm font-medium text-gray-700"
            >Video ID</label
          >
          <input
            type="text"
            id="videoId"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:ring p-2 focus:ring-opacity-50 border"
            placeholder="e.g., 76979871"
            required
          />
        </div>
        <div class="mb-4">
          <label for="title" class="block text-sm font-medium text-gray-700"
            >Title</label
          >
          <input
            type="text"
            id="title"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:ring focus:ring-opacity-50 p-2 border"
            placeholder="e.g., Rosalía — Motomami"
            required
          />
        </div>
        <div class="mb-4">
          <label
            for="description"
            class="block text-sm font-medium text-gray-700">Description</label
          >
          <textarea
            id="description"
            rows="3"
            class="mt-1 block w-full border-gray-300 rounded-md shadow-sm focus:ring focus:ring-opacity-50 p-2 border"
            placeholder="e.g., STILLZ"
          ></textarea>
        </div>

        <div>
          <button
            class="w-full bg-blue-500 text-white font-semibold py-2 px-4 rounded-md hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-opacity-50 cursor-pointer"
            type="submit"
          >
            {#if loading}
              Loading...
            {:else}
              Add Video
            {/if}
          </button>
        </div>
      </form>
    </div>
    <div class="p-4 border border-gray-400 rounded-lg bg-white shadow-md">
      <h2 class="text-2xl font-semibold">List of Videos</h2>
      <p>Manage your collection.</p>

      <div class="overflow-auto max-h-[500px]">
        {#if loading}
          <div class="text-xl font-medium text-center mt-8">Loading...</div>
        {:else if videos.length === 0}
          <p class="text-center text-gray-500">No videos found.</p>
        {:else}
          <table class="w-full mt-4">
            <thead>
              <tr>
                <th class="px-4 py-2">Sr.</th>
                <th class="px-4 py-2">Title</th>
                <th class="px-4 py-2">Vimeo Id</th>
                <th class="px-4 py-2">Description</th>
                <th class="px-4 py-2">Actions</th>
              </tr>
            </thead>
            <tbody>
              {#each videos as video, index}
                <tr>
                  <td class="border px-4 py-2"> {index + 1} </td>
                  <td class="border px-4 py-2">{video.title}</td>
                  <td class="border px-4 py-2">{video.vimeoId}</td>
                  <td class="border px-4 py-2">{video.description}</td>
                  <td class="border px-4 py-2">
                    <!-- Add action buttons here -->
                    <button
                      class="w-full bg-red-500 text-white font-semibold py-1 px-2 rounded-md hover:bg-red-600 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-opacity-50 cursor-pointer"
                      on:click={() => deleteVideo(video.id)}
                    >
                      {#if loadingDelete}
                        Deleting...
                      {:else}
                        Delete
                      {/if}
                    </button>
                  </td>
                </tr>
              {/each}
            </tbody>
          </table>
        {/if}
      </div>
    </div>
  </div>
</div>
