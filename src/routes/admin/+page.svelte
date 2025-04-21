<script lang="ts">
  import { firebaseApp } from "$lib/firebase";
  import { collection, addDoc, getFirestore } from "firebase/firestore";

  const db = getFirestore(firebaseApp);
  let loading = false;

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
</script>

<div class="bg-gray-100 min-h-screen p-4">
  <div class="p-4 border border-gray-400 rounded-lg bg-white shadow-md sm:w-xl">
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
        <label for="description" class="block text-sm font-medium text-gray-700"
          >Description</label
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
</div>
